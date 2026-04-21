# VBWEIBI 色彩能量風格美學建議系統

## 簡介

這是一個完整的色彩能量風格美學建議系統，基於 631 色彩系統。

## 🔧 GitHub Pages SPA 部署修復 (v2 - 改進版)

### 問題
GitHub Pages 在首次訪問時顯示 404，需要用戶點擊「Go Home」才能看到應用。

### 根本原因
GitHub Pages 的 404 處理機制在某些情況下可能不會立即執行 404.html 的重定向腳本。

### 解決方案
本部署包使用改進的 GitHub Pages SPA 路由解決方案：

1. **404.html** - 使用雙重機制：JavaScript 重定向 + meta refresh 備份
2. **index.html** - 包含改進的解碼腳本，更可靠地恢復 URL
3. **.nojekyll** - 防止 Jekyll 處理靜態檔案（GitHub 會隱藏此檔案，正常現象）

## 📦 檔案說明

| 檔案 | 說明 |
|------|------|
| `index.html` | 主應用程式（包含所有 UI、CSS、JavaScript 和改進的解碼腳本） |
| `404.html` | GitHub Pages 404 重定向檔案（改進版本） |
| `.nojekyll` | 告訴 GitHub Pages 不要使用 Jekyll 處理（隱藏檔案，正常） |
| `README.md` | 本說明檔案 |

## 🚀 部署步驟

### 方法 1：使用 GitHub Web 介面（推薦）

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
   - Commit message: `Fix: Improve SPA routing for GitHub Pages (v2)`
   - 點擊 `Commit changes`

4. **等待部署**
   - GitHub Pages 會自動部署（通常 1-2 分鐘）

### 方法 2：使用 Git 命令行

```bash
cd /path/to/631-color-energy
cp index.html .
cp 404.html .
cp .nojekyll .
git add index.html 404.html .nojekyll README.md
git commit -m "Fix: Improve SPA routing for GitHub Pages (v2)"
git push origin main
```

## ✅ 驗證部署

1. **等待 2-3 分鐘**
   - GitHub Pages 需要時間構建和部署

2. **清除瀏覽器快取**
   - Windows/Linux: Ctrl + Shift + Delete
   - Mac: Cmd + Shift + Delete

3. **訪問您的網站**
   - URL: `https://vbweibi.github.io/631-color-energy/`

4. **首次訪問應該直接看到應用**
   - ❌ 不應該看到 404 頁面
   - ✅ 應該直接看到色彩能量計算介面

## 🔍 技術改進

### 改進的 404.html
- 使用 JavaScript 重定向（快速、可靠）
- 添加 meta refresh 備份（以防 JavaScript 被禁用）
- 添加可見的重定向訊息和備用連結

### 改進的 index.html 解碼腳本
- 更簡潔的邏輯
- 添加調試日誌（可在瀏覽器控制台查看）
- 更好的錯誤處理

### .nojekyll 文件
- GitHub 會將其顯示為隱藏檔案（以 . 開頭）
- 這是正常現象，不影響功能
- 確保檔案已上傳到倉庫根目錄

## 📌 重要提示

- **不要修改** `index.html` 中的 `<script>` 標籤（解碼腳本）
- **不要修改** `404.html` 中的重定向路徑
- **保持** `.nojekyll` 檔案在倉庫根目錄（即使 GitHub 隱藏顯示）
- **確認** GitHub Pages 設置：
  - Settings → Pages
  - Source: Deploy from a branch
  - Branch: main, Folder: / (root)

## 🆘 故障排除

### 問題：仍然看到 404

**解決方案：**
1. 清除瀏覽器快取（Ctrl+Shift+Delete）
2. 等待 5 分鐘後重試
3. 打開瀏覽器開發者工具（F12）
4. 查看 Console 標籤，應該看到：
   - `404.html: Redirecting from ...`
   - `Restoring path from 404 redirect: ...`
5. 檢查 GitHub Pages 設置是否正確
6. 確認所有檔案都已上傳到倉庫根目錄

### 問題：頁面加載但功能不正常

**解決方案：**
1. 打開瀏覽器開發者工具（F12）
2. 檢查 Console 是否有錯誤
3. 檢查 Network 標籤中的請求是否成功

## 📞 支援

如有問題，請：
1. 檢查 GitHub Pages 設置
2. 查看瀏覽器開發者工具中的錯誤訊息
3. 確認所有檔案都在倉庫根目錄

---

**最後更新：** 2026-04-21
**版本：** SPA Fix v2.0 (Improved)
