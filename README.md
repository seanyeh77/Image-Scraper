# Image Scraper

本專案是一個基於 Python 的圖片爬取工具，可以從 Google 圖片搜尋中下載符合指定尺寸的圖片，並儲存到本地資料夾。

## 功能

- 支援從 `foodList.txt` 中讀取食物名稱列表，並逐一搜尋相關圖片。
- 支援設定最小圖片寬度與高度過濾圖片。
- 支援多線程下載，提升下載效率。
- 自動建構對應的資料夾結構。

## 安裝與使用

### 環境需求

- Python 3.8+
- 安裝以下套件：
  - `selenium`
  - `webdriver_manager`
  - `beautifulsoup4`
  - `requests`
  - `pillow`

### 安裝方式

1. 克隆專案：
   ```bash
   git clone <你的專案網址>
   cd <專案資料夾>
   ```

2. 安裝所需套件：
   ```bash
   pip install -r requirements.txt
   ```

### 建立 `foodList.txt`

建立一個名為 `foodList.txt` 的檔案，並將要搜尋的食物名稱以逗號分隔，例如：
```
蘋果,香蕉,橘子
```

### 執行程式

執行以下命令開始爬取圖片：
```bash
python <程式檔名>.py
```

爬取的圖片將會儲存在 `images/<食物名稱>` 資料夾中。

## 設定與調整

- **最小圖片尺寸**：
  在程式中調整以下變數來改變尺寸過濾條件：
  ```python
  MIN_WIDTH = 150
  MIN_HEIGHT = 150
  ```

- **滾動次數與延遲**：
  可以調整滾動次數與每次滾動的延遲：
  ```python
  scroll_page(driver, scrolls=5, delay=1)
  ```

- **最大線程數量**：
  修改多線程執行時的最大線程數：
  ```python
  max_workers=10
  ```

## 注意事項

- 此程式使用 Selenium 操作瀏覽器，須確保安裝了 Chrome 瀏覽器。
- 無頭模式下可能會有部分圖片無法正常載入，建議在開發或測試階段可以移除 `--headless` 選項。
- 本程式僅供學術與個人使用，請勿用於商業用途或違反 Google 使用條款的操作。

## 參考

- [Selenium Documentation](https://www.selenium.dev/documentation/)
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/)
- [Pillow Documentation](https://pillow.readthedocs.io/)

## 授權

本專案採用 [MIT License](LICENSE)。
