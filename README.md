# Image Scraper

## 概要

Image Scraper 是一個強大的自動圖片抓取工具，旨在幫助使用者快速搜尋並下載符合條件的圖片。專案同時提供完整的構建與打包工作流，支援多平台的應用程式打包與發佈。

---

## 開始使用

在 GitHub 頁面中，進入本專案的 [Releases](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY/releases) 頁面。

選擇最新的發佈版本。

根據您使用的操作系統下載對應的檔案：

- `my_app-windows.zip` (適用於 Windows)
- `my_app-macos.tar` (適用於 macOS)
- `my_app-linux.tar` (適用於 Linux)

解壓縮下載的檔案，並根據需要執行應用程式。

---

## 自動圖片抓取工具

### 功能

- **無頭瀏覽**：使用 Selenium WebDriver 與無頭模式的 Chrome 進行圖片抓取。
- **基於關鍵字的搜尋**：根據指定的食物名稱搜尋 Google 圖片。
- **並行執行**：同時下載多個關鍵字的圖片以節省時間。
- **尺寸驗證**：確保圖片符合最小寬度和高度的要求。

### 需求

- Python 3.10+
- 依賴項：
  - `selenium`
  - `webdriver-manager`
  - `beautifulsoup4`
  - `requests`
  - `pillow`
  - `lxml`
  - `tenacity`

### 使用方法

1. 在專案目錄下創建名為 `key_word_list.txt` 的檔案，並添加以逗號分隔的關鍵字。例如：
   ```
   apple,banana,orange
   ```
2. 執行腳本：
   ```bash
   python scraper.py
   ```
3. 圖片將保存於 `images/<food_name>` 資料夾中。

### 函式

#### `scroll_page`

滾動頁面多次以載入更多圖片。

#### `verify_image_size`

驗證圖片是否符合最小尺寸要求。

#### `search_and_download`

搜尋圖片並下載符合條件的圖片。

### 並行執行

此腳本使用 `ThreadPoolExecutor` 同時執行多個關鍵字的搜尋與下載。

---

## 構建與打包工作流

### 功能

- **多平台支持**：自動構建並打包適用於 `Windows`、`macOS` 和 `Linux` 的應用程式。
- **上傳產物**：將打包的檔案壓縮並作為 GitHub Actions 產物上傳。
- **版本化發佈**：自動生成版本號並在推送到 `main` 分支時創建 GitHub 發佈。

### 工作流細節

#### 觸發條件

- 推送到 `main` 分支。
- 針對 `main` 分支的拉取請求。

#### 構建工作

`build` 任務在以下操作系統上執行：

- `ubuntu-latest`
- `macos-latest`
- `windows-latest`

執行步驟包括：

1. **檢出程式碼**
2. **設置 Python 環境**
3. **安裝依賴項**
4. **打包應用程式**
5. **上傳產物**

#### 發佈工作

此任務僅在以下情況下創建發佈：

- 推送到 `main` 分支。

執行步驟包括：

1. **生成版本號**
2. **下載產物**
3. **創建 GitHub 發佈**

### 工作流檔案

請參考 `.github/workflows/build-and-release.yml` 以獲取實現細節。

---

## 目錄結構

```
.
├── images/                # 圖片保存目錄
├── archive/               # 壓縮檔案目錄
├── dist/                  # 構建產物目錄
├── key_word_list.txt      # 關鍵字列表檔案
├── main.py                # 應用程式進入點
├── scraper.py             # 圖片抓取腳本
├── requirements.txt       # Python 依賴項
└── .github/workflows/     # GitHub Actions 工作流
```

---

## 注意事項

- 確保已安裝 Google Chrome 和 ChromeDriver，以便 Selenium 正常工作。
- 抓取圖片時請遵守 Google 的服務條款。
- 如果需要不同的尺寸限制，可在 `scraper.py` 中調整 `MIN_WIDTH` 和 `MIN_HEIGHT` 變數。

---

## 授權

本專案採用 MIT 授權條款。

