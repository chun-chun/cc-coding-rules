# 將規則裝入專案

1. 確認規則來源和目標專案的 Git 根目錄。閱讀目標既有的 agent 指示，並檢查語言、測試、lint 與型別檢查設定。
2. 複製 `rules/core.md` 到目標的 `.coding-rules/rules/core.md`。專案含 Python 時，再複製 `stacks/python.md` 到 `.coding-rules/stacks/python.md`。從下載資料夾取用檔案，讓安裝完成後可以移除下載資料夾。
3. 在 `.coding-rules/SOURCE.md` 記錄來源、採用的規則和版本。Git 來源以 commit SHA 記錄。純下載檔優先記錄發布版本，否則用檔案的 SHA-256 記錄所用快照。
4. 用 [入口範本](templates/AGENTS.md) 把規則併入根目錄 `AGENTS.md`。保留既有文字與專案例外。若根目錄有生效的 `AGENTS.override.md`，也將入口併入該檔。只引用已複製的規則。從既有設定取得驗證指令。
5. 檢查每條引用都能在目標 repo 內解析，並檢視 diff。應提交的是規則副本、來源紀錄及專案入口。開新 Codex session，請它列出適用的規則及驗證指令。

## 更新已安裝規則

比較新來源與已安裝的版本。先保留或移出本地例外，再更新已選用的規則與來源紀錄。重跑安裝時，更新同一段入口，避免重複加入。若新版與既有約定衝突，列出差異，並將專案採用的做法寫進入口。用同樣方式驗證新版本。
