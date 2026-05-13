# Mermaid Live Preview Tool

一個即開即用的 Mermaid 圖表即時預覽工具，無需安裝任何套件。

## 功能特色

- **即時預覽** - 輸入 Mermaid 語法後即時渲染 SVG 圖表
- **錯誤提示** - 語法錯誤時顯示明確的錯誤訊息與行號
- **零安裝** - 直接在瀏覽器開啟 `preview.html` 即可使用
- **CDN 載入** - 使用 jsDelivr CDN 載入 Mermaid v11

## 使用方式

### 本機使用

直接以瀏覽器開啟 `preview.html`：

```bash
#  macOS
open preview.html

# Linux
xdg-open preview.html

# Windows
start preview.html
```

### GitHub Pages

部署後可透過以下網址存取：

```
https://tryweb.github.io/mermaid-preview/preview.html
```

## 支援的圖表類型

Mermaid 支援多種圖表類型，包含但不限於：

| 類型 | 語法關鍵字 |
|------|-----------|
| 流程圖 | `flowchart` |
| 時序圖 | `sequenceDiagram` |
| 甘特圖 | `gantt` |
| 類別圖 | `classDiagram` |
| 狀態圖 | `stateDiagram-v2` |
| 實體關係圖 | `erDiagram` |
| 旅程圖 | `journey` |
| 餅圖 | `pie` |

## 專案結構

```
.
├── preview.html              # 主要應用檔案
├── .github/workflows/
│   └── deploy.yml            # GitHub Actions 自動部署設定
├── docs/
│   └── github-pages-setup.md # GitHub Pages 手動設定說明
└── README.md                 # 本文件
```

## 部署

本專案使用 GitHub Actions 自動部署到 GitHub Pages：

- 推送至 `main` 分支時自動觸發
- 也可手動從 Actions 頁面觸發

詳細設定說明請參考 [docs/github-pages-setup.md](docs/github-pages-setup.md)

## 技術細節

- **Mermaid v11** - 透過 ESM CDN 載入
- **純前端** - 無需後端服務
- **即時渲染** - 300ms debounce 避免過度渲染

## License

MIT
