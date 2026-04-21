# VBWEIBI 色彩能量風格美學建議系統

## 簡介

這是一個完整的色彩能量風格美學建議系統，基於 631 色彩系統。

## 🔧 GitHub Pages SPA 部署修復

### 問題
GitHub Pages 在首次訪問時顯示 404，需要用戶點擊「Go Home」才能看到應用。

### 解決方案
本部署包使用標準的 GitHub Pages SPA 路由解決方案：

1. **404.html** - 當 GitHub Pages 找不到頁面時，將 URL 編碼到 sessionStorage 並重定向到 index.html
2. **index.html** - 包含解碼腳本，在頁面加載時從 sessionStorage 恢復原始 URL
3. **.nojekyll** - 防止 Jekyll 處理靜態檔案

## 📦 檔案說明

| 檔案 | 說明 |
|------|------|
| `index.html` | 主應用程式（包含所有 UI、CSS、JavaScript 和解碼腳本） |
| `404.html` | GitHub Pages 404 重定向檔案 |
| `.nojekyll` | 告訴 GitHub Pages 不要使用 Jekyll 處理 |
| `README.md` | 本說明檔案 |

## 🚀 部署步驟

### 方法 1：使用 GitHub Web 介面（推薦新手）

1. **進入您的 GitHub 倉庫**
   - https://github.com/VBWEIBI/631-color-energy

2. **上傳檔案**
   - 點擊 `Add file` → `Upload files`
   - 拖拽以下檔案：
     - `index.html`
     - `404.html`
     - `.nojekyll`
     - `README.md`

3. **提交更改**
   - Commit message: `Fix: Implement proper SPA routing for GitHub Pages`
   - 點擊 `Commit changes`

4. **等待部署**
   - GitHub Pages 會自動部署（通常 1-2 分鐘）

### 方法 2：使用 Git 命令行

```bash
# 進入倉庫目錄
cd /path/to/631-color-energy

# 複製檔案
cp index.html .
cp 404.html .
cp .nojekyll .

# 提交
git add index.html 404.html .nojekyll README.md
git commit -m "Fix: Implement proper SPA routing for GitHub Pages"
git push origin main
```

## ✅ 驗證部署

1. **等待 2-3 分鐘**
   - GitHub Pages 需要時間構建和部署

2. **訪問您的網站**
   - URL: `https://vbweibi.github.io/631-color-energy/`

3. **首次訪問應該直接看到應用**
   - ❌ 不應該看到 404 頁面
   - ✅ 應該直接看到色彩能量計算介面

4. **測試功能**
   - 輸入主格數、加值數、願望數
   - 查看結果
   - 切換版本和加值數
   - 截圖保存結果

## 🔍 技術細節

### SPA 路由工作原理

1. **用戶訪問** `https://vbweibi.github.io/631-color-energy/some-path`
2. **GitHub Pages** 找不到該路徑，返回 404
3. **404.html** 被執行，將完整 URL 保存到 `sessionStorage`
4. **404.html** 重定向到 `index.html`
5. **index.html** 加載，執行解碼腳本
6. **解碼腳本** 從 `sessionStorage` 恢復原始 URL
7. **應用** 正常運行，React Router 處理路由

### 為什麼需要 .nojekyll？

GitHub Pages 預設使用 Jekyll 處理靜態檔案。由於我們的應用是純 HTML/CSS/JavaScript，不需要 Jekyll 處理，`.nojekyll` 檔案告訴 GitHub Pages 跳過 Jekyll 處理，加快部署速度。

## 📌 重要提示

- **不要修改** `index.html` 中的 `<script>` 標籤（解碼腳本）
- **不要修改** `404.html` 中的重定向路徑
- **保持** `.nojekyll` 檔案在倉庫根目錄
- **如果** 404 問題仍然存在，檢查 GitHub Pages 設置：
  - Settings → Pages
  - Source: Deploy from a branch
  - Branch: main, Folder: / (root)

## 🆘 故障排除

### 問題：仍然看到 404

**解決方案：**
1. 清除瀏覽器快取（Ctrl+Shift+Delete）
2. 等待 5 分鐘後重試
3. 檢查 GitHub Pages 設置是否正確
4. 確認所有三個檔案都已上傳到倉庫根目錄

### 問題：頁面加載但功能不正常

**解決方案：**
1. 打開瀏覽器開發者工具（F12）
2. 檢查 Console 是否有錯誤
3. 檢查 Network 標籤中的請求是否成功

## 📞 支援

如有問題，請：
1. 檢查 GitHub Pages 設置
2. 查看瀏覽器開發者工具中的錯誤
3. 確認所有檔案都在倉庫根目錄

---

**最後更新：** 2026-04-21
**版本：** SPA Fix v1.0
