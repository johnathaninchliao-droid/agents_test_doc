# 例外處理 (Exception Handling) 核心指南

**例外處理（Exception Handling）** 是程式設計中用來處理「執行時期錯誤（Runtime Error）」的重要機制。當程式遇到非預期狀況（例如檔案不存在、網路斷線、除以零）時，系統會拋出「例外」。若未妥善處理，程式會直接崩潰中斷；透過例外處理，程式可以在出錯時優雅地復原或給予提示。

---

## 一、 為什麼需要例外處理？

1. **避免程式無預警崩潰**：提升軟體的穩定性與容錯能力（Fault Tolerance）。
2. **分離正常流程與錯誤處理**：讓主要商業邏輯清晰，把錯誤應對集中管理。
3. **確保資源正確釋放**：無論程式是否出錯，都能安全關閉資料庫連線、開啟的檔案或釋放記憶體。
4. **易於除錯與維護**：可記錄詳細的錯誤日誌（Log）與堆疊追蹤資訊（Stack Trace）。

---

## 二、 核心運作架構與關鍵字

多數現代程式語言皆具備類似的控制結構：

| 關鍵字 (Python / 其他語言) | 角色功能 |
| :--- | :--- |
| **`try`** | 包裹「可能發生例外」的程式區塊。 |
| **`except` / `catch`** | 當 `try` 區塊發生特定錯誤時執行相應的處理邏輯。 |
| **`else`** *(Python)* | 僅在 `try` 區塊**完全沒有發生例外**時執行。 |
| **`finally`** | 無論是否發生錯誤，**最後必定會執行**的清理區塊。 |
| **`raise` / `throw`** | 手動主動拋出例外。 |

---

## 三、 程式範例

### 1. Python 範例

```python
def divide_numbers():
    try:
        dividend = float(input("請輸入被除數: "))
        divisor = float(input("請輸入除數: "))
        result = dividend / divisor
    except ZeroDivisionError:
        print("錯誤：除數不能為 0！")
    except ValueError:
        print("錯誤：請輸入有效的數字！")
    except Exception as e:
        print(f"發生未預期的錯誤: {e}")
    else:
        print(f"計算成功，結果為: {result}")
    finally:
        print("運算作業結束。\n")

if __name__ == "__main__":
    divide_numbers()
```

### 2. JavaScript / TypeScript 範例

```javascript
function fetchUserData(userId) {
  try {
    if (!userId) {
      throw new Error("無效的 User ID！");
    }
    console.log(`正在取得使用者 ${userId} 的資料...`);
    // 模擬可能出錯的運作
  } catch (error) {
    console.error(`捕捉到錯誤: ${error.message}`);
  } finally {
    console.log("清理連線資源完成。");
  }
}
```

---

## 四、 例外處理的最佳實踐 (Best Practices)

- **捕捉具體的例外類型**：
  避免使用無差別的通用捕捉（如 Python 的裸 `except:` 或 Java 的 `catch (Exception e)`），以免無意中掩蓋語法錯誤或記憶體耗盡等嚴重問題。
- **避免「靜默忽略」錯誤**：
  不要寫出空的 catch/except 區塊；至少應記錄 Log 或提示使用者。
- **善用資源管理器（Context Managers）**：
  在支援的語言中優先使用自動釋放資源的語法，例如 Python 的 `with open(...)` 或 Java 的 `try-with-resources`，減少手寫 `finally` 洩漏資源的風險。
- **保持 `try` 區塊精簡**：
  只把真正可能拋出例外的敘述放進 `try` 區塊，避免混入過多程式碼導致定位錯誤困難。
