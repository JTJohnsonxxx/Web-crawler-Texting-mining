# Web-crawler-Texting-mining
主要是紀錄網路爬蟲（ PTT & FB )的 script，以及爬蟲後的斷詞與文字雲應用、關鍵字分群等 text mining 探勘技術。  
因此只有 Master，沒有其他的 branches，多數為紀錄自己開發的專案  

1. Ptt_Crawler.ipynb: PTT爬蟲，從 open source 參考爬蟲後，改寫部分 for 研究使用。  
  A. 目的是讓非開發者可以自行爬取，因此拉出簡單的 UI 板塊，讓 User 只要輸入要爬取的「PTT 版名」、「要爬取的總頁數」、「開始爬得起始頁數」  
  B. 包含自動翻頁、爬取間隔(0.05sec)防止被當做DDoS、benchmark等等功能  
  C. 輸出包含：文章作者、內容、日期、回文數（含：總回文數、推文減噓文數、推文數、噓文數、中立回文數）、回文內容、文章標題  
  
2. 社團爬蟲進階版抓reactions_0319-2.py: FB 社團爬蟲，為自行開發。主要是從 Graph API 端點 request 資料，並儲存至 local。  
  A. 拉出非常簡單的 UI 板塊，讓 User 輸入 token 和 目標頁面的 id 即可爬取  
  B. 從發文的序列爬取，包含發文的回文，回文的回文等等。含自動翻頁、自動輸出csv等功能  
  C. 輸出包含：發文id、回文id、作者姓名、作者id、回文內容、回文時間  
  
3. wordcloud.ipynb: 文字雲輸出 for 台灣危險駕駛的性別研究，這邊僅紀錄 wordcloud、collections 的 Counter 用法  
  A. 研究目的：為了瞭解男女性別危險駕駛的真實狀況，因此從八卦版爬取三百篇文章內文包含女駕駛被評為三寶的文章，並把文章斷詞後找出詞頻製作出以「車」為意象的背景圖片的文字雲，藉以用資料視覺化的方式協助觀測論壇中多數回文者對女性駕駛的刻板印象  
   <img src="https://github.com/JTJohnsonxxx/Web-crawler-Texting-mining/blob/master/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202020-08-29%20%E4%B8%8B%E5%8D%882.55.23.png" width="800">  
  B. 後續從內政部警政署拿到歷年台灣車禍紀錄的資料，發現從民國 93年至今107年的數據均顯示 A1類道路交通事故死亡人數（A1類係指造成人員當場或24小時內死亡之交通事故），男性均顯著高於女性。（男性歷年平均約為 72%)  
      <img src="https://github.com/JTJohnsonxxx/Web-crawler-Texting-mining/blob/master/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202020-08-29%20%E4%B8%8B%E5%8D%882.42.49.png" width="200">  
  C. 結論：男性危險駕駛反而更嚴重，不因針對特定性別貼上三寶標籤   
    
4. keywords_clutering_V0.1( normalize ).ipynb: 關鍵字分群研究，為自行開發的專案。主要目的是探索外部搜尋關鍵字 與 Users 閱讀特定文章的行為關係  
流程包含： 從 local 載入資料、稀疏矩陣加速運算效率、EDA、numpy 轉陣列加速運算、sklearn kmeans 進行分群  
