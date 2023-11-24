# Credit-Card-Fraud-Detection
## Competition
This competition, hosted on [T-Brain](https://tbrain.trendmicro.com.tw/Competitions/Details/31) by 玉山銀行(E.SUN Bank), is focused on credit card fraud detection. Participants are granted access to de-identified customer transaction records containing patterns that signify potential fraudulent activities. The challenge requires participants to engineer algorithms and construct models aimed at recognizing suspicious transactional behavior. The ultimate goal is to elevate the efficiency of identifying and preventing fraudulent misuse of credit cards.

## Dataset
As the dataset is exclusively reserved for competition use, it remains inaccessible to the public.   
However, it comprises various features relevant to credit card transactions, showcasing anonymized information essential for modeling credit card fraud detection.  

### Features
| Feature Name | Description (Chinese)|
|------------|--------------------|
| txkey      | 交易序號           |
| locdt      | 授權日期           |
| loctm      | 授權時間           |
| chid       | 顧客ID             |
| cano       | 交易卡號           |
| contp      | 交易類別           |
| etymd      | 交易型態           |
| mchno      | 特店代號           |
| acqic      | 收單行代碼         |
| mcc        | mcc_code         |
| conam      | 交易金額-台幣      |
| ecfg       | 網路交易註記       |
| insfg      | 是否分期交易       |
| iterm      | 分期期數           |
| bnsfg      | 是否紅利交易       |
| flam1      | 實付金額           |
| stocn      | 消費地國別         |
| scity      | 消費城市           |
| stscd      | 狀態碼             |
| ovrlt      | 超額註記碼         |
| flbmk      | Fallback註記       |
| hcefg      | 支付型態           |
| csmcu      | 消費地幣別         |
| csmam      | 消費地金額         |
| flg_3dsmk  | 3D交易註記         |
| **label**      | **盜刷與否**    |

The most critical feature, **label**, signifies the presence or absence of credit card fraud, serving as the target variable for model training and evaluation.  

## Evaluate
The competition utilizes the **F1-score** as the primary evaluation metric for assessing model performance. 

$$
\text{F1-score} = 2 \frac{\text{precision} \times \text{recall}}{\text{precision} + \text{recall}}
$$

- TP: True Positive - Transactions correctly identified as fraud  
- FN: False Negative - Transactions identified as normal while being fraud  
- FP: False Positive - Transactions identified as fraud while being normal  
- TN: True Negative - Transactions correctly identified as normal  

- **Precision** measures the accuracy of the model in correctly identifying transactions flagged as fraudulent among all the transactions it flagged as fraudulent.
$$\text{Precision} = \frac{\text{TP}}{\text{TP + FP}}$$  
  
- **Recall** evaluates the model's capability to identify all actual fraudulent transactions among all the transactions that are, in reality, fraudulent.
$$\text{Recall} = \frac{\text{TP}}{\text{TP + FN}}$$
