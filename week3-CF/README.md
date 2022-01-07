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

## 使用平台、工具
平台：Colab

語言：Python（套件：pandas / gzip, json / sklearn / re ）

## 推薦方法
### 協同過濾

* **User-based CF**
   * 將ratings資料集轉成dict
   * 將評論數量較少的user刪去，以減少運算負擔
   * dict轉置成矩陣後計算user similarity，找出相似的user
   * 從相似user的評論商品中，依序排列產生推薦清單
   * 不足條件而推薦清單為空者(新user)，改為使用rule-based推薦過去銷量最好的商品

* **Item-based CF**
   *


* **Surprise package CF**
   *



## 專案結果


推薦方法             | 評估分數             
--------------------|:-------------------:
User-based CF + Rule-based  | 
Item-based CF + Rule-based  |
Surprise CF + Rule-based    |

