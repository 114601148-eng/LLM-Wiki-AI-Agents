# LLM Wiki × 教學型 HTML 簡報：AI Agents 入門

本專案以 AI Agents 為主題，使用 Colab + GitHub 建立可重跑的知識整理流程。

## 專案內容
- `sources/`：5 份資料來源與初始摘要（符合至少 ingest 5 篇）
- `wiki/`：LLM Wiki 知識頁
- `output/AI_Agents_教學簡報.html`：可離線瀏覽的 8 頁教學簡報
- `LLM_Wiki_AI_Agents.ipynb`：Colab 工作流程，包含來源擷取、Wiki 整理、品質檢查與輸出

## 在 GitHub + Colab 使用
1. 在 GitHub 建立一個 Public 或 Private repository，例如 `llm-wiki-ai-agents`。
2. 將本資料夾所有內容上傳到 repository（保留資料夾結構）。
3. 在 GitHub 開啟 `LLM_Wiki_AI_Agents.ipynb`，點右上角 **Open in Colab**；或在 Colab 選 File → Open notebook → GitHub，貼上 repo URL。
4. 在 Colab 依序執行 notebook。Notebook 會嘗試從 5 個來源網址擷取網頁文字；若來源網站擋爬蟲或格式不相容，會保留已附的來源摘要，並在 log 標記 fallback。
5. 執行後會在 `wiki/` 產生更新後的頁面，在 `output/` 產生 HTML 簡報與檢查紀錄。
6. 將 Colab 產生的檔案下載後，回到 GitHub 上傳／commit，即可形成可分享的成果連結。

## GitHub Pages（公開 HTML）
若要讓 HTML 有公開網址：Repository → Settings → Pages → Deploy from a branch → `main` / `/root`（或將 HTML 放在 root）→ Save。若放在 `output/`，可將檔案複製到 root 或設定 Pages 對應資料夾。部署完成後會取得 `https://<帳號>.github.io/<repo>/AI_Agents_教學簡報.html` 類型網址。

## Loop / Graph 設計
資料取得 → Wiki 查詢／整理 → 內容驗證 → HTML 生成 → 瀏覽測試。
- 內容驗證失敗：回到 Wiki 整理或來源取得，最多兩輪。
- HTML 測試失敗：回到 HTML 生成，修正後重測。
- 成功條件：至少 5 個來源、Wiki 頁面存在、簡報包含教學結構、來源清單完整、HTML 可開啟且投影片數量正確。

## 重要誠實說明
此範本已提供 5 份來源索引、初始摘要、Wiki 與簡報。Notebook 的即時網頁擷取結果會依網站當下存取狀況記錄；若要聲稱「實際成功 ingest」，請以你在 Colab 執行後產生的 `execution_log.md` 為準，不要把 fallback 說成成功抓到全文。
