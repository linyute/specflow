# Claude Code 提示：將 AI 編程社群智慧整合進 SpecFlow.com

## 專案背景
我需要在 specflow.com 網站新增「社群智慧」專區，展示 Reddit 社群洞察下 AI 協助軟體開發實踐的演化。我已分析 2024 年 1 月至 2025 年 6 月間 47 篇 Reddit 貼文，並產生三份摘要 markdown 文件。原始資料也以 CSV 檔保存，供驗證與進一步分析。

## 資料來源
1. **主要資料來源**：`commmunity_wisdom/railway_public_posts.csv`（47 篇貼文，7 欄：標題、內容、作者、subreddit、分數、建立時間、網址）
2. **摘要文件**（由 CSV 分析產生）：
   - `commmunity_wisdom/timeline.md` - 2024-2025 AI 編程實踐的時間演化
   - `commmunity_wisdom/guide-evolution.md` - 編程指南與方法論演化分析
   - `commmunity_wisdom/syntopical-summary.md` - 主題、貢獻者與未來趨勢綜合分析

## 關鍵任務：資料驗證
在網站功能實作前，需驗證摘要文件是否忠實反映 CSV 資料：

### 驗證清單
1. **關鍵指標核對**：
   - 貼文總數（應為 47）
   - 日期範圍（2024/1/4 - 2025/6/4）
   - subreddit 分布（r/cursor: 25, r/ChatGPTCoding: 14, r/ClaudeAI: 5）
   - 最高分貼文是否與 CSV 資料一致

2. **貼文交叉比對**：
   - 確認摘要提及的前 5 名貼文在 CSV 中存在且分數正確
   - 驗證作者歸屬與貼文數
   - 檢查所有 Reddit 連結是否正確

3. **時間分析驗證**：
   - 核對每季貼文數是否與 CSV 相符
   - 確認各時期平均分數
   - 驗證突破性貼文的時間排序

4. **額外洞察提取**：
   - 找出摘要未涵蓋的重要貼文
   - 發掘貼文內容中未被捕捉的模式
   - 從高分貼文擷取精確引用，作為特色亮點

## 網站結構需求

### 1. 在 Quarto 網站 Learn 區新增 `/community-wisdom/` 專區
此專區需可由主導覽 Learn 下拉選單進入，包含：
- 首頁總覽與分頁導覽
- 互動式時間軸視覺化
- 可搜尋的指南庫，含完整貼文內容
- 關鍵洞察儀表板，能即時計算 CSV 資料
- 貢獻者亮點，完整貼文歷史

### 2. 資訊架構
```
/community-wisdom/
├── index.html (總覽與介紹)
├── /data/
│   ├── posts.json (由 CSV 產生)
│   ├── timeline.json (驗證後的時間軸資料)
│   └── contributors.json (作者統計)
├── /timeline/
│   ├── index.html (互動式時間軸)
│   └── /api/ (資料端點)
├── /guides/
│   ├── index.html (分類指南列表)
│   ├── /vibe-coding/
│   ├── /multi-agent/
│   ├── /api-integration/
│   └── /post/{id}/ (單篇貼文頁)
├── /insights/
│   ├── index.html (關鍵發現儀表板)
│   └── /trends/ (新興趨勢視覺化)
└── /contributors/
    ├── index.html (頂尖貢獻者與影響)
    └── /{username}/ (個別貢獻者頁)
```

### 3. 資料處理流程

#### 第一階段：CSV 資料擷取與驗證
```typescript
// 1. 解析 CSV，建立主資料結構
const posts = parseCSV('railway_public_posts.csv');

// 2. 與摘要比對驗證
const validation = {
  totalPosts: posts.length === 47,
  dateRange: validateDateRange(posts),
  subredditCounts: validateSubredditDistribution(posts),
  topPosts: validateTopPosts(posts, summaryData),
  metrics: calculateMetrics(posts)
};

// 3. 產生完整 JSON 資料庫
const database = {
  posts: enrichPostData(posts),
  timeline: generateTimelineData(posts),
  contributors: calculateContributorStats(posts),
  categories: categorizePostsWithML(posts),
  validation: validation
};
```

#### 第二階段：內容增強
- 從貼文內容擷取關鍵引用（特別是高分貼文）
- 根據內容分析產生標籤
- 建立全文搜尋索引（含貼文內容）
- 建立貼文間關聯圖（引用、主題相似）

### 4. 主要功能

#### A. 互動式時間軸元件（CSV 資料）
- 即時計算 CSV 指標
- 顯示實際貼文分布，不只摘要數
- 滑鼠懸停顯示貼文標題與分數
- 點擊可看完整貼文內容（來自 CSV）
- 資料驗證指示，顯示摘要與原始資料一致/不一致

#### B. 強化指南庫
- 標題與內容全文搜尋（來自 CSV）
- 顯示完整貼文內容，不只摘要
- 類別自動由內容分析產生
- 「前往 Reddit」連結並追蹤
- 依內容相似推薦相關貼文

#### C. 即時洞察儀表板
- CSV 資料即時計算：
  - 實際 517% 成長驗證
  - 分數分布長條圖
  - 發文頻率熱圖
  - 作者貢獻模式
- 比較摘要與實際資料

#### D. 完整貢獻者展示
- 每位作者完整貼文歷史（來自 CSV）
- 頂尖作者貢獻時間軸
- 分數趨勢分析
- 依貼文內容分析主題專長

### 5. 資料驗證實作

建立驗證報告頁面，顯示：
```typescript
{
  "summaryAccuracy": {
    "timeline": {
      "claimedPosts": 47,
      "actualPosts": countFromCSV(),
      "match": true/false
    },
    "topPosts": {
      "claimed": [...summaryTopPosts],
      "actual": [...csvTopPosts],
      "discrepancies": [...]
    },
    "metrics": {
      "growthRate": {
        "claimed": "517%",
        "calculated": calculateFromCSV(),
        "variance": "..."
      }
    }
  }
}
```

### 6. 進階資料處理任務

1. **CSV 主要處理**：
   ```typescript
   // 擷取並驗證所有資料
   - 正確解析 CSV（日期處理）
   - 清理並標準化文字內容
   - 驗證所有 Reddit 連結
   - 為每篇貼文產生唯一 ID
   - 從高分貼文內容擷取引用
   ```

2. **與摘要交叉驗證**：
   ```typescript
   // 比對摘要與 CSV 資料
   - 摘要提及貼文與 CSV 記錄比對
   - 驗證分數、日期、作者
   - 標記需人工審查的差異
   - 產生驗證報告
   ```

3. **強化 JSON 結構**：
   ```json
   {
     "posts": [{
       "id": "generated-uuid",
       "csvRow": 1,
       "title": "貼文標題",
       "body": "CSV 完整貼文內容",
       "author": "使用者名稱",
       "score": 420,
       "date": "2025-05-09",
       "created_at": "2025-05-09T12:34:56Z",
       "url": "https://reddit.com/...",
       "subreddit": "ClaudeAI",
       "category": ["vibe-coding", "guides"],
       "keyQuotes": ["擷取的精采引用..."],
       "validationStatus": "verified|discrepancy|not_in_summary"
     }],
     "validation": {
       "summaryAccuracy": 95.2,
       "discrepancies": [...],
       "additionalInsights": [...]
     }
   }
   ```

### 7. 實作優先順序（更新版）

**第一階段（資料基礎）**：
1. 解析並驗證 CSV 資料
2. 與摘要文件交叉比對
3. 產生完整 JSON 資料庫
4. 建立驗證報告頁面
5. 設定資料更新流程

**第二階段（核心功能）**：
1. 用真實 CSV 資料實作時間軸
2. 建立可搜尋的完整貼文庫
3. 建立即時洞察儀表板
4. 部署並顯示資料驗證指示

**第三階段（進階體驗）**：
1. 加入貢獻者深度分析
2. 實作內容相似度分析
3. 建立貼文關聯視覺化
4. 加入 CSV 資料匯出功能

### 8. 其他需求

#### 資料完整性
- 顯示「來源：Reddit 社群資料」與貼文數
- 顯示最後更新日期
- 各頁顯示資料驗證狀態
- 提供處理後資料集下載連結

#### 搜尋強化
- 索引 CSV 完整貼文內容
- 實作模糊搜尋（容錯）
- 可依日期範圍搜尋
- 可依最低分數篩選

#### 分析整合
- 追蹤最常被點擊貼文
- 監控搜尋查詢
- 量測各指南停留時間
- 報告資料驗證準確率

### 9. 測試需求（強化版）

- CSV 解析正確性（支援多種編碼）
- 資料驗證報告正確性
- 47 篇貼文全文搜尋功能
- 載入完整貼文內容的效能
- 所有 Reddit 連結驗證
- 摘要與 CSV 交叉比對正確性

## 檔案位置
- CSV 資料來源：`railway_public_posts.csv`
- 摘要 markdown 檔案：[請提供 timeline.md、guide-evolution.md、syntopical-summary.md 位置]
- 目前網站根目錄：[請提供網站目錄路徑]
- 現有 CSS/JS 資源：[請提供可重用路徑]

## 其他補充
[請補充網站技術棧、設計系統或限制]

## Claude Code 初始任務
1. 先載入並檢查 CSV 檔，了解資料結構
2. 驗證摘要文件與 CSV 資料，並回報差異
3. 從高分貼文內容擷取額外洞察
4. 由 CSV 產生完整 JSON 資料庫
5. 建立驗證報告頁面
6. 再進行社群智慧專區建置

請先載入 CSV 檔，驗證摘要內容，並建立完整資料擷取計畫，再開始網站功能實作。

---

**免責聲明**：本文件由 [GitHub Copilot](https://docs.github.com/copilot/about-github-copilot/what-is-github-copilot) 翻譯為繁體中文，可能包含錯誤。如發現不適當或錯誤之翻譯，請至 [issue](../../issues) 回報。
