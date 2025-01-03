## Data Flow Diagram 0

```mermaid
flowchart TD
    用戶[用戶] -->|提供資料| 系統[處理: 系統]
    系統 -->|分析結果| 用戶
    醫療人員[醫療人員] -->|查詢資料| 系統
    系統 -->|預測報告| 醫療人員
    系統 -->|儲存數據| 資料庫[(資料庫)]
```

## Data Flow Diagram

```mermaid
flowchart TD
    %% 外部實體與處理
    User[外部實體: 用戶] -->|提供註冊資訊| Process1[處理: 用戶註冊與登入]
    Process1 -->|儲存用戶資料| DataStore1[(資料庫: 用戶資料庫)]
    Process1 -->|登入成功，導向首頁| User

    User -->|啟動步態分析請求| Process2[處理: 即時步態分析]
    Process2 -->|獲取步態數據| Camera[外部實體: 攝影機]
    Camera -->|傳回數據| Process2
    Process2 -->|分析結果顯示| User
    Process2 -->|儲存步態數據| DataStore2[(資料庫: 步態數據)]

    MedicalStaff[外部實體: 醫療人員] -->|查詢患者數據| Process3[處理: 病情風險預測]
    Process3 -->|提取數據| DataStore2
    Process3 -->|病情風險預測結果| MedicalStaff
    Process3 -->|儲存風險預測結果| DataStore3[(資料庫: 風險報告)]
```

### 說明：
- **註冊與登入**：
  - 使用者將註冊或登入資訊發送給處理模組，系統驗證後儲存至用戶資料庫，並回應登入成功。
- **即時步態分析**：
  - 使用者啟動步態分析，系統從攝影機獲取數據，進行分析並顯示結果，同時將步態數據儲存到資料庫。
- **病情風險預測**：
  - 醫療人員查詢患者的步態數據，系統從資料庫提取並進行風險預測，回應結果並儲存至風險報告資料庫。

