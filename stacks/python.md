# Python 開發規則

## 型別與公開契約

公開函式的參數與回傳型別沿用專案慣例。改動契約時，檢查呼叫者和既有型別檢查結果。

例如：`load_orders(path: Path) -> list[Order]` 若改成回傳分頁結果，需一起調整原本直接迭代清單的呼叫端與介面文件。

## 例外處理

捕捉此處能處理的例外類型。轉換例外時，用 `raise ... from exc` 保留原因。

```python
try:
    data = json.loads(text)
except json.JSONDecodeError as exc:
    raise ValueError("訂單內容不是有效 JSON") from exc
```

這個轉換適用於入口約定以 `ValueError` 表達輸入錯誤的情境；實際例外類型依專案契約選擇。

## 設定物件

需要將多個相關參數一起傳遞時，沿用專案的設定表示方式，為參數群組命名。若使用 dataclass，可用不可變物件避免單次覆寫影響共享預設；不要為採用範例而重寫既有設定系統。

```python
from dataclasses import dataclass, replace

@dataclass(frozen=True)
class DownloadConfig:
    timeout: float = 10.0
    retry_count: int = 3

normal_config = DownloadConfig()
slow_source_config = replace(normal_config, timeout=30.0)
```

此例只建立另一組設定，`normal_config.timeout` 仍為 `10.0`。日誌、共用功能與資源管理的原則見 [共用規則](../rules/core.md)。
