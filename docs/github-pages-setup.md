# GitHub Pages 部署說明

## 自動部署流程

本專案已設定 GitHub Actions workflow (`.github/workflows/deploy.yml`)，會在以下情況觸發部署：

- 推送程式碼到 `main` 分支
- 手動觸發 workflow dispatch

## 手動設定步驟

### 1. 啟用 GitHub Pages

1. 前往你的 GitHub 專案頁面
2. 點擊 **Settings** → **Pages**
3. 在 **Source** 區塊，選擇 **GitHub Actions**（不是 "Deploy from a branch"）
4. 等待 workflow 首次執行完成

### 2. 確認 Workflow 權限

1. 前往 **Settings** → **Actions** → **General**
2. 確保 **Workflow permissions** 設定為 **Read and write permissions**
3. 如果使用預設的 "Read repository contents and packages permissions"，需確認 `pages: write` 權限已授予

### 3. 分支設定

- 預設部署分支為 `main`
- 如果你的主要分支是 `master` 或其他名稱，請修改 `.github/workflows/deploy.yml` 中的 `branches` 設定：

```yaml
on:
  push:
    branches:
      - master  # 修改為你的分支名稱
```

### 4. 驗證部署

首次推送後：

1. 前往 **Actions** 標籤頁，確認 workflow 執行成功
2. 前往 **Settings** → **Pages**，查看部署狀態
3. 部署成功後，你的網站將可透過以下網址存取：
   ```
   https://<username>.github.io/<repository-name>/preview.html
   ```

## 手動觸發部署

如果不想推送程式碼也能觸發部署：

1. 前往 **Actions** 標籤頁
2. 點擊 **Deploy to GitHub Pages** workflow
3. 點擊 **Run workflow** → **Run workflow**

## 故障排除

| 問題 | 解決方式 |
|------|----------|
| Workflow 未觸發 | 檢查分支名稱是否與 `deploy.yml` 設定相符 |
| 部署失敗：Permission denied | 確認 Actions 權限設定為 Read and write |
| 頁面顯示 404 | 等待數分鐘讓 GitHub Pages 生效，確認 URL 正確 |
| 舊版部署殘留 | 前往 Settings → Pages，確認 Source 已設為 GitHub Actions |

## 檔案結構

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions 部署設定
├── docs/
│   └── github-pages-setup.md  # 本說明文件
└── preview.html            # 主要部署檔案
```
