# Credit-Card-Fraud-Detection
## Competition
https://tbrain.trendmicro.com.tw/Competitions/Details/31

## Dataset
Due to the dataset being restricted for competition use only, it is not available for public access.  
### Features
| 欄位列名       | 中文說明               |
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


## Evaluate
Use **F1-score** to evaluate the performance.    

$$
\text{F1-score} = 2 \frac{\text{precision} \times \text{recall}}{\text{precision} + \text{recall}}
$$

- TP: True Positive - Transactions correctly identified as fraud  
- FN: False Negative - Transactions identified as normal while being fraud  
- FP: False Positive - Transactions identified as fraud while being normal  
- TN: True Negative - Transactions correctly identified as normal  

$$\text{Precision} = \frac{\text{TP}}{\text{TP + FP}}$$  

$$\text{Recall} = \frac{\text{TP}}{\text{TP + FN}}$$
