精聯電子維修報價單資訊提取工具－多張 PDF 批次測試版
版本：2026-11-04（批次資料同步＋檔案清單獨立捲動版）

【本測試版用途】
這是一個獨立的 GitHub Pages 測試專案，不會修改既有 Catch-Quotation 網頁或其 GitHub Repository。
可一次選取多張 PDF，逐張判讀，列出每張 PDF 的 SR 單號與缺漏欄位，最後將所有成功判讀的資料依既有 Google Sheet 欄位順序合併下載成一份 CSV。檔名工具列不固定於頂端；左側檔案清單使用獨立捲軸，可在清單區塊內拖曳捲動，不影響右側判讀結果。

【檔案】
index.html       網頁主畫面
app.js           PDF 文字／座標判讀、批次處理與 CSV 匯出
style.css        檔案清單獨立捲動，右側判讀結果維持原本頁面捲動方式
style.css        畫面樣式
.nojekyll        避免 GitHub Pages 將靜態資源交由 Jekyll 處理

【建立新的 GitHub Repository】
1. 登入 GitHub：https://github.com/
2. 右上角「＋」→ New repository。
3. Repository name 建議輸入：Catch-Quotation-Batch-Test
4. 選擇 Public（GitHub Free 使用 GitHub Pages 時，公開 Repository 可直接使用）。
5. 可勾選 Add a README file，然後按 Create repository。
6. 進入新 Repository 的 Code 頁面，按 Add file → Upload files。
7. 解壓縮本 ZIP，將 index.html、app.js、style.css、.nojekyll、README.txt 全部拖曳上傳至 Repository 根目錄（不要把外層資料夾整個上傳）。
8. 在頁面下方按 Commit changes。

【啟用 GitHub Pages】
1. 在新 Repository 上方選 Settings。
2. 左側選 Pages。
3. Build and deployment 的 Source 選 Deploy from a branch。
4. Branch 選 main，資料夾選 /(root)，按 Save。
5. 等待 GitHub Actions 部署完成；回到 Settings → Pages，按 Visit site。
6. 網址格式為 https://你的GitHub帳號.github.io/Catch-Quotation-Batch-Test/
   若沿用原專案帳號 miechen-try，網址預期為：
   https://miechen-try.github.io/Catch-Quotation-Batch-Test/

【批次測試方式】
1. 開啟新網頁，按「選擇 PDF」一次選取多張報價單，或將多張 PDF 拖曳到上傳區。
2. 系統先建立每張 PDF 的獨立批次紀錄並依序判讀，完成後載入第一張 PDF 預覽及判讀欄位。
3. 在「批次判讀與 CSV 匯出」區查看每張檔案的 SR 單號、判讀狀態與缺漏欄位。
4. 若顯示「待確認」，請回到單張判讀區檢查第一張；其他檔案目前以批次檢查表提示缺漏，並非逐張提供可編輯畫面。
5. 右側欄位每次輸入或變更都會即時同步到目前 PDF 的獨立紀錄；切換檔案前亦會再次同步。
6. 切回先前檔案時會載入最後修改的欄位值，不會重新解析並覆蓋手動修改；左側「文字擷取・X/13 欄位」及異常底色會即時更新。
7. 按「下載整批 CSV」前會再次同步目前畫面，CSV 依每張 PDF 最後保存的資料匯出。
6. Google 試算表選「檔案」→「匯入」→「上傳」→選擇 CSV。依需求選擇新增工作表或取代目前工作表。第一次測試建議先匯入新的空白工作表核對欄位。

【重要注意事項】
- 本測試版沿用既有 Catch-Quotation 的欄位解析與 Google Sheet 列拆分邏輯；批次功能仍屬測試，請先用已確認內容的 PDF 小批量驗證，不要直接覆蓋正式帳務資料。
- CSV 不額外加入欄位標題列，維持原本貼到 Google Sheet 的欄位位置（B 至 O 欄，共 14 欄）。
- 每張 PDF 若含多筆 SR／多台設備／多筆零件，會依既有程式規則拆成資料列；實際配對仍應核對批次結果及匯入後資料。
- PDF 預設在使用者瀏覽器本機解析，不會上傳到本網站伺服器。PDF.js 與 Tesseract OCR 透過 CDN 載入，因此首次使用需要網路連線。
- GitHub Pages 是公開網站。請勿把含客戶個資的 PDF、測試報價單或實際 CSV 上傳到 GitHub Repository；只在網頁操作時由本機選取檔案。
- 若 PDF 是掃描影像，OCR 辨識可能不完整；請特別檢查 SR 單號、設備序號、故障原因、廠商檢測回覆與零件金額。

【回報問題時請提供】
1. 原始 PDF（若含個資，請先確認可分享或遮蔽）。
2. 批次結果顯示的缺漏欄位截圖。
3. CSV 匯入後錯誤的列與預期內容。


本次介面更新（2026-11-04）：檔名工具列已設為 sticky，向下捲動檔案清單或判讀內容時仍固定在視窗頂端；按鈕順序為「下載整批 CSV」→「複製報價單檔名」→「清除」。
