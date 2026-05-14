# 數獨遊戲 (Sudoku Game)

## 檔案資訊

- **檔案名稱**: sudoku.html
- **檔案類型**: HTML
- **行數**: 238 行
- **語言**: zh-TW (繁體中文)

## 功能說明

這是一個基於 HTML/CSS/JavaScript 的數獨遊戲，提供以下功能：

- 隨機生成數獨謎題
- 點擊格子選擇並輸入數字
- 數字鍵盤輸入 (1-9 及清除)
- 檢查答案功能
- 新遊戲功能

## 程式結構

### HTML 結構

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>數獨遊戲</title>
    <style>...</style>
</head>
<body>
    <h1>數獨遊戲</h1>
    <div id="game-container">
        <div id="board"></div>
    </div>
    <div id="numpad">...</div>
    <div id="controls">
        <button onclick="newGame()">新遊戲</button>
        <button onclick="checkSolution()">檢查</button>
    </div>
    <div id="message"></div>
    <script>...</script>
</body>
</html>
```

### CSS 樣式

| 選擇器 | 說明 |
|--------|------|
| `body` | 字體、Flexbox 置中、背景色 #f5f5f5 |
| `#board` | 9x9 網格，每個格子 40px，深色邊框 |
| `.cell` | 格子樣式：白色背景、字體 20px、游標 pointer |
| `.cell.fixed` | 固定數字格子：灰色背景 #e0e0e0、粗體 |
| `.cell.selected` | 選中格子：淺藍色背景 #b3d9ff |
| `.cell.error` | 錯誤格子：紅色文字 |
| `#numpad` | 數字鍵盤：3 欄網格 |
| `.num-btn` | 數字按鈕：50x50px、字體 24px |

### JavaScript 函式

| 函式名稱 | 參數 | 說明 |
|----------|------|------|
| `generateSudoku()` | 無 | 生成完整的數獨解答 (基於基礎謎題並進行行列變換) |
| `shuffle(arr)` | arr | Fisher-Yates 洗牌演算法 |
| `transpose(m)` | m | 矩陣轉置 |
| `shuffleRows(m)` | m | 隨機打亂 3x3 區塊內的行 |
| `removeNumbers(grid, count)` | grid, count | 從完整謎題中移除指定數量數字 |
| `newGame()` | 無 | 開始新遊戲：生成謎題、移除 45 個數字、渲染棋盤 |
| `renderBoard()` | 無 | 將 board 陣列渲染為 DOM 元素 |
| `selectCell(r, c)` | r, c | 選擇格子並高亮顯示 |
| `inputNumber(num)` | num | 輸入數字到選中的格子 (0 表示清除) |
| `checkSolution()` | 無 | 檢查玩家答案是否正確，標記錯誤格子 |

### 全域變數

| 變數名稱 | 類型 | 說明 |
|----------|------|------|
| `board` | Array | 當前遊戲狀態 (9x9 二維陣列) |
| `solution` | Array | 完整解答 (9x9 二維陣列) |
| `selectedCell` | DOM Element | 目前選中的格子元素 |

## 遊戲邏輯

1. **生成謎題**: 使用預設的基礎數獨，透過矩陣轉置和區塊內行列隨機交換來生成不同的謎題
2. **移除數字**: 隨機移除 45 個數字形成謎題
3. **輸入數字**: 點擊格子選擇後，使用數字鍵盤輸入 1-9 或清除
4. **檢查答案**: 比對當前 board 與 solution，標記錯誤格子並顯示訊息

## 變更記錄

| 日期 | 變更內容 |
|------|----------|
| 2026-04-02 | 初始版本建立 |
