# 維護 CC Coding Rules

- 跨專案的原則寫在 `rules/core.md`，語言特有的規則放在 `stacks/`。
- 可從外層 SAI 的 `coding_style.md` 和 `ARCHITECTURE.md` 找例子。先確認能跨專案重用，再抽成規則。專案命令、模組名稱、路徑及 Reporter 契約留在 SAI。
- 每條規則寫清楚適用情境和預期行為。適合由工具驗證的部分，指出用哪類檢查。
- 修改檔名或安裝方式時，同步檢查 `README.md`、`INSTALL.md` 和入口範本的路徑。
- 維護此 repo 時，將安裝與驗證限制在測試目錄。將規則套用到外層 SAI 屬另一項操作。
