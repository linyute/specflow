這裡根據 Reddit 資料，整理 AI 編程「操作指南」的結構化演化。

# AI 編程操作指南的演化

## 第一階段：基礎（2024 年 9 月－2025 年 2 月）

### 概述
此階段約 6 個月，重點在建立與 AI 協作編程的基本原則。該時期指南不再只教 AI 產生程式碼，而是教開發者如何結構化與 AI 的協作。主題包括建立 AI 的心智模型（如角色扮演或初階開發者）、設定專案規則，以及用測試驅動開發（TDD）作為 AI 產生程式碼的安全網。核心創新是將 AI 從搜尋引擎轉變為可程式化的協作者。

### 重要指南

#### 1. 角色扮演以產生結構化產出
- **來源**：u/illusionst（r/ClaudeAI，分數：410） - [https://reddit.com/r/ClaudeAI/comments/1fbp2a5/the_lazy_programmers_guide_to_ai_coding/](https://reddit.com/r/ClaudeAI/comments/1fbp2a5/the_lazy_programmers_guide_to_ai_coding/)
- **目標族群**：初學者／中階
- **核心步驟**：
    1.  **扮演軟體工程師**：「先請 AI 扮演軟體工程師，傳遞所有相關檔案，並請它解釋程式碼給你聽。」
    2.  **扮演產品經理**：「接著換上產品經理帽子，請 AI 也這麼做。這時你要明確說明新功能需求，並可要求產品需求文件。」
    3.  **扮演技術主管**：「若功能較複雜，可先寫偽程式碼，讓 AI 再次檢視程式碼庫、需求，並判斷需修改哪些檔案與程式碼段落。」
    4.  **扮演開發者**：「最後請 AI 根據偽程式碼及前述理解，寫出實際程式碼。完成後請 AI 產生 git commit 訊息。」
- **工具**：Cursor 編輯器、Python、FastAPI、Postgres
- **創新**：本指南首創「角色扮演工作流程」，用戶分配不同專業角色給 AI，獲得特定類型產出（分析、規劃、編程），突破了 AI 行為控制。

#### 2. 在大型專案中用 TDD 與文件
- **來源**：u/Kirmark（r/cursor，分數：137） - [https://reddit.com/r/cursor/comments/1ikq9m6/cursor_ide_setup_and_workflow_in_larger_projects/](https://reddit.com/r/cursor/comments/1ikq9m6/cursor_ide_setup_and_workflow_in_larger_projects/)
- **目標族群**：中階／進階
- **核心步驟**：
    1.  **先寫測試再寫程式碼**：「我用 1-2 個整合測試搭配真實憑證。先寫失敗測試、實作功能、取得檢查點……這建立了高效 AI 反饋迴路。」
    2.  **將任務拆成小步驟**：「找到合適任務大小最重要……太大 Cursor 會偏離主題，太小則花太多時間寫測試。」
    3.  **將思路文件化**：「我把所有討論與決策存成設計文件並提交程式碼……可隨時開新對話，加入設計文件作脈絡，從任意點繼續。」
    4.  **只用 Composer Agent 工作**：「能回溯任意對話狀態、修改提示、自動還原檔案並重試，極為強大。」
- **工具**：Cursor IDE（Composer Agent）、SuperWhisper（語音輸入）
- **創新**：本指南建立了 AI 在專業大型專案的最佳實踐。首創用 TDD 作 AI 反饋迴路，並將聊天紀錄正式文件化以維持脈絡。

## 第二階段：發展（2025 年 3 月－5 月初）

### 概述
此階段出現大量結構化、完整指南。社群將「氛圍編程」流程編成詳細、可重複的工作流程。主題是**脈絡管理與明確指令**。指南教用戶建立專案規則、提供相關程式碼範例、將複雜功能拆成數十個小提示。「把 AI 當初階開發者」成為主流心智模型，強調引導而非盲信。

### 重要指南

#### 1. 終極「氛圍編程」手冊
- **來源**：u/PhraseProfessional54（r/ClaudeAI，分數：420） - [https://reddit.com/r/ClaudeAI/comments/1kivv0w/the_ultimate_vibe_coding_guide/](https://reddit.com/r/ClaudeAI/comments/1kivv0w/the_ultimate_vibe_coding_guide/)
- **目標族群**：中階
- **核心步驟**：（18 步驟結構化總覽）
    1.  **規劃**：定義願景、先規劃 UI/UX、精通 Git、選擇主流技術棧。
    2.  **設定**：善用 Cursor Rules，維護有文件的 `instructions` 資料夾。
    3.  **執行**：撰寫詳細提示、拆解複雜功能、明智管理聊天脈絡（新功能開新對話）。
    4.  **精進**：隨時重啟提示、精確提供檔案脈絡、善用現有元件保持一致性。
    5.  **品質保證**：反覆用 AI 檢查安全與效能、遵循安全最佳實踐、用日誌系統化除錯。
    6.  **AI 管理**：明確防止未預期變更（如「不要更動未指定內容」），並維護「AI 常見錯誤」文件。
- **工具**：Cursor、Gemini 2.5 Pro、Claude、v0.dev、Git、Next.js、Supabase、Tailwind CSS
- **創新**：本指南成為**AI 協助開發的事實標準**，將零散技巧整合為涵蓋專案管理、編程、安全、除錯的完整流程。

#### 2. 「初階開發者」心智模型
- **來源**：u/eastwindtoday（r/cursor，分數：112） - [https://reddit.com/r/cursor/comments/1k5826a/cursor_is_like_a_junior_dev_guide_it_step_by_step/](https://reddit.com/r/cursor/comments/1k5826a/cursor_is_like_a_junior_dev_guide_it_step_by_step/)
- **目標族群**：初學者／中階
- **核心步驟**：
    1.  **定義用戶可執行內容**：「我從用戶體驗出發。」
    2.  **將功能拆成小任務**：「每個任務都要 Cursor 能一次完成。」
    3.  **每步寫明確指令**：「包含輸入、輸出、程式碼位置。」
    4.  **編程前先設置 Cursor 規則**：「引導 AI 遵循專案特定模式。」
    5.  **每步完成即測試**：「有問題就隔離並針對問題重跑提示。」
    6.  **持續逐步推進**：「不會一次請它建構整個儀表板或後端。」
- **工具**：Cursor、Notion、Devplan
- **創新**：本指南普及了**「初階開發者」比喻**，幫助用戶理解為何需要明確、逐步引導 AI 編程助手。

## 第三階段：進階（2025 年 5 月底－6 月）

### 概述
最新階段標誌著工程化開發流程本身。指南高度精細，將 AI 視為可程式化代理人，置於更大系統中。重點在打造可延展、半自動化流程，能高保真處理龐大脈絡與複雜度。這些指南針對進階用戶，目標是建構生產級 AI 驅動系統。

### 重要指南

#### 1. 代理式專案管理
- **來源**：u/Cobuter_Man（r/cursor，分數：35） - [https://reddit.com/r/cursor/comments/1l2p2y6/agentic_project_management_my_ai_workflow/](https://reddit.com/r/cursor/comments/1l2p2y6/agentic_project_management_my_ai_workflow/)
- **目標族群**：進階
- **核心步驟**：
    1.  **啟動階段**：用「管理者代理人」（如 Claude 3.7、GPT-4o）啟動提示，理解專案目標並建立詳細實作計畫，將工作拆分給「實作代理人」。
    2.  **主迴圈**：請管理者代理人建立「任務分配提示」給第一個任務，貼到新對話（實作代理人）。實作代理人完成任務，將成果記錄到「動態記憶庫」（markdown 檔），並回報。
    3.  **審查與迭代**：請管理者代理人審查記憶庫，然後給後續提示（如除錯或進行下一任務）。
    4.  **脈絡交接**：當代理人脈絡快滿時，指示執行「交接程序」，建立 `Handover_File.md` 與 `Handover_Prompt.md`，無縫傳遞脈絡到新代理人（新對話）。
- **工具**：Cursor（或其他 AI IDE）、高階模型（Claude 3.7、GPT-4o）、便宜模型負責實作、GitHub。
- **創新**：本指南首創正式**多代理人專案管理框架**，明確分工與溝通協定（記憶庫、交接程序），克服脈絡限制並協調複雜工作。

#### 2. 用版本控制錨定 AI 脈絡
- **來源**：u/aarontatlorg33k（r/cursor，分數：29） - [https://reddit.com/r/cursor/comments/1l00f5y/manifestmd_workflow_statemd_gitshas_god_mode/](https://reddit.com/r/cursor/comments/1l00f5y/manifestmd_workflow_statemd_gitshas_god_mode/)
- **目標族群**：進階
- **核心步驟**：
    1.  **啟用 AI 提交**：指示 Cursor 每次任務前後都備份，可能會自動產生 Git commit。
    2.  **追蹤 commit SHA**：每完成一個重要任務，找出 Cursor（或你）產生的 Git commit SHA。
    3.  **更新清單**：將 GitSHA 加到 `.cursor/manifest.md` 或 `workflow_state.md`，直接記在已完成任務旁（如：`- [x] 建立登入表單 - GITSHA: def5678`）。
    4.  **用 SHA 除錯**：功能失敗或需修正時，用 SHA 跳回最後正常狀態，指示 AI「從那一刻繼續」或「參考 SHA `abc1234` 的程式碼」。
- **工具**：Cursor、Git
- **創新**：本指南首創**將 Git SHA 整合進 AI 工作清單**，讓 AI 理解精確、可驗證的狀態，完美回溯並大幅提升除錯與回歸能力。

## 演化總結

### 技術進展
- **基礎期**：社群學會不再把 AI 當黑盒子，開始用軟體工程原則引導。重點是**角色扮演提示**與用**TDD**驗證 AI 產出。
- **發展期**：重點轉向建立高度詳細、可重複流程。關鍵概念包括**「初階開發者」心智模型**、完整**`.cursorrules` 檔**、功能拆解為**原子任務**，以及精細**脈絡提供**（引用類似檔案）。
- **進階期**：現狀是工程化整個 AI 開發環境，包括建立**多代理人系統**、產生**「脈絡即程式碼」**（專屬 AI 摘要文件），並將 AI 直接整合版本控制系統以管理狀態。

### 創新時間軸
- **2024 年 9 月 7 日**：**角色扮演工作流程**於 [https://reddit.com/r/ClaudeAI/comments/1fbp2a5/the_lazy_programmers_guide_to_ai_coding/](https://reddit.com/r/ClaudeAI/comments/1fbp2a5/the_lazy_programmers_guide_to_ai_coding/) 首次提出
- **2024 年 12 月 20 日**：**多模型工作流程**（推理模型規劃、實作模型編程）於 [https://reddit.com/r/ChatGPTCoding/comments/1hinwsr/the_goat_workflow/](https://reddit.com/r/ChatGPTCoding/comments/1hinwsr/the_goat_workflow/) 首次提出
- **2025 年 2 月 8 日**：**TDD 作 AI 反饋迴路**於 [https://reddit.com/r/cursor/comments/1ikq9m6/cursor_ide_setup_and_workflow_in_larger_projects/](https://reddit.com/r/cursor/comments/1ikq9m6/cursor_ide_setup_and_workflow_in_larger_projects/) 分享
- **2025 年 3 月 24 日**：**每日工作流程（`.cursorrules` 與類似檔案脈絡）**於 [https://reddit.com/r/ChatGPTCoding/comments/1jiyzro/my_cursor_ai_workflow_that_actually_works/](https://reddit.com/r/ChatGPTCoding/comments/1jiyzro/my_cursor_ai_workflow_that_actually_works/) 詳述
- **2025 年 5 月 9 日**：**終極 18 步氛圍編程指南**於 [https://reddit.com/r/ClaudeAI/comments/1kivv0w/the_ultimate_vibe_coding_guide/](https://reddit.com/r/ClaudeAI/comments/1kivv0w/the_ultimate_vibe_coding_guide/) 發表
- **2025 年 5 月 26 日**：**半自動脈絡產生**（建立 `ai_module_summary.md`）於 [https://reddit.com/r/cursor/comments/1kvl1aw/my_workflow_for_generating_and_maintaining_deep/](https://reddit.com/r/cursor/comments/1kvl1aw/my_workflow_for_generating_and_maintaining_deep/) 首次提出
- **2025 年 5 月 31 日**：**GitSHA 整合脈絡錨定**於 [https://reddit.com/r/cursor/comments/1l00f5y/manifestmd_workflow_statemd_gitshas_god_mode/](https://reddit.com/r/cursor/comments/1l00f5y/manifestmd_workflow_statemd_gitshas_god_mode/) 首次提出
- **2025 年 6 月 3 日**：**代理式專案管理框架**於 [https://reddit.com/r/cursor/comments/1l2p2y6/agentic_project_management_my_ai_workflow/](https://reddit.com/r/cursor/comments/1l2p2y6/agentic_project_management_my_ai_workflow/) 詳述

---

**免責聲明**：本文件由 [GitHub Copilot](https://docs.github.com/copilot/about-github-copilot/what-is-github-copilot) 翻譯為繁體中文，可能包含錯誤。如發現不適當或錯誤之翻譯，請至 [issue](../../issues) 回報。
