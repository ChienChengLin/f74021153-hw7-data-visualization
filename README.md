# PTTonitor / PTT使用者多重分身帳號關係圖

[網頁連結點此](https://chienchenglin.github.io/f74021153-hw7-data-visualization/)

## 呈現目標
&ensp; PTT，全名批踢踢實業坊，為台灣影響力數一數二的網路社群，擁有超過2萬個分類看板，
註冊帳號高達150萬，是台灣原創網路文化的誕生地。<br/>

&ensp; 曾經有市長候選人的幕僚成立PTT官方帳號，為了要和選民更加貼近，最後反被鄉民起底，
爆發多重分身帳號的疑雲；近幾年的重大社會事件，如洪仲丘案、太陽花學運等，更是讓
PTT單日上線人次突破千萬。然而，其中這些帳號，真的都是鄉民的心聲嗎？又或者只是為
了帶起輿論風向、為了發文洗版進而稀釋重大新聞事件，而產生的分身帳號呢？<br/>

&ensp; 本次作業的目標在於找出特定PTT用戶的分身帳號，並以d3.js視覺化呈現分身帳號間的網
路關係圖，同時輔以每個帳號的詞頻泡泡圖，以呈現該帳號的用詞習慣。


## 使用技術
- [d3.js](https://d3js.org/)
- [jquery](https://jquery.com/)
- [bootstrap](http://getbootstrap.com/)


## 設計流程
### Python爬取資料 & 前置資料處理
- 利用Scrapy爬取網頁版PTT的貼文、回文等相關資訊
- 利用Telnetlib連線至BBS版PTT，爬取所有帳號之上站位址、時間等資訊
- 將前述資料作進一步處理及分析，得到分身帳號群的關係資料(存為json file)與帳號對應之詞頻分布(存為csv file)

### d3.js & jquery進行資料視覺化
- 將分身帳號的關係以d3之directed force graph呈現
- 將帳號的詞頻分布以d3之force bubble chart呈現
- 以使用過相同IP位址的使用者作為節點(Nodes)
- 若節點間的上站活動時間相當接近或用詞相似度達一定值，則畫上鏈結(Links)
- 鏈結粗細與用詞相似程度成正比
- 若鏈結具有箭頭，則代表兩節點有貼文回文之互動關係
- 將游標移到鏈結上，會顯示用詞相似度及回文互動關係的tooltip
- 點擊節點則會在右側區塊顯示詞頻泡泡圖
- 泡泡圖的大小隨著用詞頻率越高而增大
- 可隱藏的圖例

## 測試瀏覽器
- Safari
- Google Chrome
