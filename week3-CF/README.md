# Collaborative filtering
## 專案目的
利用2014年Amazon發布的兩份資料集，建立Collaborative filtering推薦系統，根據使用者的過去的購買項目中預測未來可能會購買的商品組合，以達到增加銷售商品項目及提高利潤的成果
## 資料集介紹
1. All_Beauty.csv：提供使用者購買商品的紀錄（此次未使用）
2. meta_All_Beauty.json.gz：提供商品的基本資訊
      
## 資料切分
根據時間將資料分割為訓練資料及測試資料：
* 訓練資料 - 2018-09-01之前的購買紀錄
* 測試資料 - 2018-09-01至2018-09-30之間的購買紀錄

## 資料清理
刪除ratings資料集中重複評論筆數：9069筆

## 使用平台、工具
平台：Colab

語言：Python（套件：pandas / gzip, json / scikit-surprise ）

## 推薦方法
### 協同過濾

* **User-based CF**
   * 將ratings資料集轉成dict
   * 將評論數量較少的user刪去，以減少運算負擔
   * 因大部分user之間的評分沒有交集，因此轉置成矩陣後計算user similarity，找出相似的user
   * 從相似user的評論商品中，依序排列產生推薦清單
   * 不足條件而推薦清單為空者(新user)，改為使用rule-based推薦過去銷量最好的商品

* **Item-based CF**
   * 將ratings資料集轉成dict
   * 因大部分商品和被user評分之間的關係沒有交集，轉置成矩陣減輕運算負擔
   * 計算商品被user評分的相似度ˋitem similarity matrixˋ
   * 找出每個 user 有評分過的商品之後，依據相似程度找出與該商品相似的商品
   * 不足條件而推薦清單為空者(新user)，改為使用rule-based推薦過去銷量最好的商品

* **Surprise package CF**
   * 因效能問題，僅保留ratings六個月內的資料
   * 過濾ratings中重複的資料，僅時間上留下最新的一筆
   * 將資料讀成Surprise的格式
   * 使用Surprise模型計算出推薦清單


## 專案結果


推薦方法             | 評估分數             
--------------------|:-------------------:
User-based CF + Rule-based  | 0.10588235294117647
Item-based CF + Rule-based  | 0.09491525423728814
Surprise CF + Rule-based    | 0.00169491525423729

