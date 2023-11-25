# Credit Card Fraud Detection
## Data Process
### 1. Rename column titles
```js
new_column_titles = [
    "交易序號", "授權日期", "授權時間", "顧客ID", "交易卡號", "交易類別", "交易型態",
    "特店代號", "收單行代碼", "mcc_code", "交易金額-台幣", "網路交易註記", "是否分期交易",
    "分期期數", "是否紅利交易", "實付金額", "消費地國別", "消費城市", "狀態碼", "超額註記碼",
    "Fallback註記", "支付型態", "消費地幣別", "消費地金額", "3D交易註記", "盜刷與否"
]
```

### 2. Process null data

**- Fill with the most frequent values**
- 交易型態
- mcc_code
- 消費地國別
- 支付型態
```js
train_df['交易型態'].fillna(train_df['交易型態'].mode()[0], inplace=True)
train_df['mcc_code'].fillna(train_df['mcc_code'].mode()[0], inplace=True)
train_df['消費地國別'].fillna(train_df['消費地國別'].mode()[0], inplace=True)
train_df['支付型態'].fillna(train_df['支付型態'].mode()[0], inplace=True)
```

**- Remove rows with missing values**
-  消費城市
```js
train_df.dropna(subset=['消費城市'], inplace=True)
```

### 3. Simplify features
- 消費地幣別
Converting the currency code 70 to 1 while assigning 0 for any other code.
```js
train_df['消費地幣別'] = np.where(train_df['消費地幣別'] == 70, 1, 0)
test_df['消費地幣別'] = np.where(test_df['消費地幣別'] == 70, 1, 0)
```

### 4. Process Authorization Time (授權時間)
- Extracting only the **hours** and storing them in a new column named '授權時間-小時'.   
- Removes the original '授權時間' column.
```js
def convert_to_hms(seconds):
    hours = seconds // 10000
    minutes = (seconds % 10000) // 100
    seconds = seconds % 100
    return hours, minutes, seconds

train_df['授權時間-小時'] = train_df['授權時間'].apply(lambda x: convert_to_hms(x)[0])
test_df['授權時間-小時'] = test_df['授權時間'].apply(lambda x: convert_to_hms(x)[0])

train_df.drop(columns=['授權時間'],inplace=True)
test_df.drop(columns=['授權時間'],inplace=True)
```

### 5. Count repeated values as new features.
- Card Transaction Count (卡片交易次數)   
Count the number of transactions associated with each unique card number. 

- Store Transaction Count (特店交易次數)

- Customer Transaction Count (顧客交易次數

- 卡片一日交易次數

- 一日購買相同商品次數

- (卡片)購買商品次數

*這個部分我應該要把train和test一起統計的:(  

### 6. Drop features
- 交易序號
- 狀態碼
- 授權日期

