# 簡介

多吃水果有益身體健康，不過該怎麼挑選選水果才是既健康又經濟呢？

這是一個以R語言建立的應用，使用者只要安裝此套件並執行run_fruitRank函數即可透過以Shiny建立的互動介面，輕鬆地查詢**當日**的水果CP值排行榜。

由於水果價格每日浮動，透過此CP值排行即可快速的協助使用者進行購買決策。

# 安裝
```
library(devtools)

install_github("sulaxd/fruitRank")
```

# 執行
```
library(fruitRank)

run_fruitRank()
```

# 資料來源

1. [農產品行情](http://m.coa.gov.tw/OpenData/FarmTransData.aspx)

1. [食品營養成分](https://consumer.fda.gov.tw/Food/TFND.aspx?nodeID=178#)

1. [衛生福利部國民健康署](http://www.hpa.gov.tw/BHPNet/Web/healthtopic/TopicArticle.aspx?No=201308300011&parentid=201205100003)

#  分數計算說明

    參考衛生福利部國民健康署提供之『國人膳食營養素參考攝取量』，制定男女各年齡層及身孕狀況之每日各營養素建議量(**表1**)。

依據**食品營養成分**提供之『食品營養成份資料庫』與**農產品行情**提供之各類水果當日批發價，求得當日各水果每100克所含有的各營養成分份量(**表2**)及其價格。

給定各營養成分之權重，維生素系列各為**10%**，葉酸及菸鹼素各為**10%**，鈣、磷、鎂、鐵與鋅各為**2%**。

當使用者選擇某年齡層、性別與身孕狀況後，依據其條件將表1篩選為**表3**，並將表2各水果營養份量值除以表3，求得各水果每100克可提供單日所需營養建議值之比例。

對各營養成份進行標準化後，將各水果的各營養成份Z分數值乘上各自之權重，並乘上10，將水果單位從每100克提升為每1000克。接下來，對各水果的營養成分變數值進行加總後，除以每日各水果之每公斤批發價，可得到各類水果每公斤所含的總營養加總分數。

最後，進行平移及標準化，使分數值易於閱讀及解釋。


