# ⚙️ 故事創作標準作業流程 (Standard Operating Procedure)

為了確保小說的品質、邏輯嚴密性以及角色的一致性，我們採用「多重 Agent 協作與自我修正」的工作流。每一章節的誕生都必須經過以下四個階段。

### 👥 團隊成員速查表
**⚠️ 在執行以下任何階段前，AI 必須先讀取對應 Agent 的定義檔，以載入其完整的工作守則與前置讀取清單。**

| 角色 | 定義檔 | 參與階段 |
|---|---|---|
| 🗺️ 劇情大綱規劃師 | [`Agent_OutlineArchitect.md`](./Agent_OutlineArchitect.md) | 階段一 |
| ✍️ 首席主筆 | [`Agent_LeadWriter.md`](./Agent_LeadWriter.md) | 階段二、三 |
| 🕵️‍♂️ 世界觀與邏輯監督員 | [`Agent_LoreChecker.md`](./Agent_LoreChecker.md) | 階段二（審核） |
| 🧠 角色心理架構師 | [`Agent_CharacterPsychologist.md`](./Agent_CharacterPsychologist.md) | 階段二（審核） |
| 🎨 美術總監 | [`Agent_ArtDirector.md`](./Agent_ArtDirector.md) | 按需呼叫（見下方說明） |

## 階段一：大綱建構與人工審定 (Outline & Plan Phase)
在撰寫正文前，大綱規劃師必須先建構嚴謹的章節大綱，且必須經過總導演（用戶）人工確認。

1. **前置檢核：** **🗺️ 劇情大綱規劃師**（→ 讀取 [`Agent_OutlineArchitect.md`](./Agent_OutlineArchitect.md)）必須強制完整讀取以下檔案，以防止源頭出錯：
   * **世界觀底線**：`Story_Bible.md`（故事聖經）、`01_Settings/world_rules.md`、`01_Settings/bug_biology.md`、`01_Settings/factions_and_society.md`。這確保大綱一開始就掛上「廢土戰損與色氣」濾鏡。
   * **角色驅動力**：`02_Characters/` 中的所有角色設定檔，確保大綱情節符合角色性格與核心動機。
   * **劇情銜接點**：`03_Outlines/main_plot.md`（確認主線地圖與章節定位）與 `03_Outlines/story_progress.md`（確認上一章的結尾動態記憶），確保劇情完美銜接。
2. **產出大綱草案 (Draft Plan)：** 規劃師產出包含「場景、互動、情緒曲線、建議字數」的章節節拍 (Beats) 草案，並**先在對話中呈現**供總導演審查（若字數過長，可先寫入暫存檔 `03_Outlines/chapter_[X]_plan_draft.md`），**不直接寫入正式大綱檔案**。
3. **人工微調與確認：** 總導演針對草案提出修改意見，AI 進行調整，直到滿意為止。
4. **正式定稿寫入：** 當總導演發出「確認大綱，寫入正式檔案」指令後，AI 才會將最終大綱寫入 `03_Outlines/chapter_[X]_plan.md`，並**自動清除 any 暫存草案檔案**。

---

## 階段二：逐段撰寫與即時審核迴圈 (Write & Review Loop)
本階段是一個**寫作→審核→修正→通過→下一段**的連續迴圈。**✍️ 首席主筆**（→ 讀取 [`Agent_LeadWriter.md`](./Agent_LeadWriter.md)）嚴格遵循已定案的 `chapter_[X]_plan.md`，逐個節拍 (Beat by Beat) 撰寫初稿，**每完成一個 Beat 立即進入內部審核**，通過後才推進下一個 Beat。

### 撰寫
1. **首席主筆** 根據大綱中的當前節拍 (Beat)，以本作的寫作風格（極致的感官描寫、直白露骨的細節與肉體描寫、平民視角），撰寫該段初稿。

### 即時審核
每完成一個 Beat 的初稿，立即進入以下雙重審核：

2. **🕵️‍♂️ 邏輯監督員**（→ 讀取 [`Agent_LoreChecker.md`](./Agent_LoreChecker.md)）檢查：
   * **世界觀合規性**：是否違反 `01_Settings/` 與 `Story_Bible.md` 的設定底線？
   * **劇情連貫性**：是否有邏輯漏洞？**是否與 `story_progress.md` 發生前後章節矛盾（吃書現象）？**
   * **外界反應**：環境、群眾或自然規則的反應是否合理？
3. **🧠 心理架構師**（→ 讀取 [`Agent_CharacterPsychologist.md`](./Agent_CharacterPsychologist.md)）檢查：
   * **美學與性格一致性**：角色的言行舉止是否符合 `02_Characters/` 中的設定？是否發生 OOC (Out of Character)？
   * **角色狀態**：核心角色的特質是否自然展現而無割裂感？配角的反應是否真實？

### 修正與迭代
4. **高效迭代與人工裁決：** 
   - 主筆根據兩位專家的意見進行「自我修正」，並重新送審。
   - **⚠️ 安全限制**：此修正迴圈上限為 **3 ~ 5 次**。若達到上限仍未達完美，AI 必須**暫停並主動向總導演回報卡關原因**（例如設定衝突），由總導演裁決，嚴防無效的重複生成與 Token 浪費。

### 通過與自動推進
5. **單段獨立輸出**：審核通過的 Beat 會暫存為 `04_Manuscript/chapter_[X]-[Y].md`（例如：第一章第二個 Beat 存為 `chapter_1-2.md`）。
6. **自動推進**：AI 將無須等待總導演確認，**自動回到本階段開頭**，接續撰寫下一個 Beat，直到該章節所有 Beats 撰寫完畢。

---

## 階段三：章節整合與最終拋光 (Merge & Polish Phase)
當一章的所有分段 Beats 都完成後，進行整合：

1. **整合合併**：**✍️ 首席主筆**（→ [`Agent_LeadWriter.md`](./Agent_LeadWriter.md)）將零散的 `chapter_[X]-[Y].md` 合併為單一的完整章節檔案 `04_Manuscript/chapter_[X].md`。
2. **流暢度潤飾**：主筆對整篇文章進行語氣連貫性、過渡段落與重複用詞的最終修飾與拋光。
3. **清理暫存**：清理零散的 `chapter_[X]-[Y].md` 暫存檔。
4. **進度更新**：嚴格依照標準化模板，將關鍵劇情摘要追加寫入 `03_Outlines/story_progress.md`。

---

## 階段四：人工驗收與 Git 存檔 (Approval & Git Phase)
1. **總導演驗收**：總導演閱讀並確認 `04_Manuscript/chapter_[X].md`。
2. **🛑 自主 Git 禁令**：**除非總導演明確發出指令（例如：「更新至 Git」、「提交存檔」），否則 AI 在任何階段皆不得主動在背景執行 `git commit` 或 `git push` 等版本控制操作。**

---

## 按需呼叫：美術總監 🎨
**🎨 美術總監**（→ 讀取 [`Agent_ArtDirector.md`](./Agent_ArtDirector.md)）不參與固定的四階段流程，而是由**總導演在任何階段隨時呼叫**，用於：
* 為關鍵場景、角色外貌或世界觀元素生成視覺概念圖
* 確認角色的視覺設定（如烙印位置、服裝損壞狀態）是否與文字描述一致

---

## 🚀 如何觸發此 SOP (總導演專用指令)

> **💡 提示：** 在每次**新對話**開始時，建議先讓 AI 讀取本 SOP，確保它了解完整的工作流程。專案根目錄的 [`AGENTS.md`](../AGENTS.md) 會作為 AI 的入口導航。

### 🔰 指令零：啟動寫作會話（新對話時使用）
**「請讀取 AGENTS.md 和 Workflow_SOP.md，進入寫作模式。」**
*AI 將讀取入口檔與 SOP，載入團隊成員速查表與流程規範，準備接收後續指令。*

---

### 🎯 指令一：規劃新章節大綱（觸發階段一）
**「請呼叫大綱規劃師，規劃第 [X] 章大綱：[填寫劇情重點]」**
*AI 將：*
1. *讀取 `Agent_OutlineArchitect.md` 載入規劃師的工作守則與前置讀取清單*
2. *依清單讀取 `Story_Bible.md`、`01_Settings/` 全部設定檔、`02_Characters/`、`main_plot.md`、`story_progress.md`*
3. *產出大綱草案並等待您的修改*

### ✍️ 指令二：確認大綱並開始寫作（觸發階段二→三自動推進）
**「大綱確認，開始執行第 [X] 章的撰寫與審核。」**
*AI 將：*
1. *把大綱定稿寫入 `03_Outlines/chapter_[X]_plan.md`*
2. *讀取 `Agent_LeadWriter.md`、`Agent_LoreChecker.md`、`Agent_CharacterPsychologist.md`*
3. *進入「寫 Beat → 雙重審核 → 修正 → 下一段」迴圈，直到所有 Beats 完成*
4. *自動進入階段三：合併、潤飾、清理暫存、更新 `story_progress.md`*

---

### 🔍 指令三：單獨呼叫審核（不重寫，僅檢查）
**「請呼叫邏輯監督員/心理架構師，檢查以下內容：[貼上文字或指定檔案]」**
*AI 將讀取對應的 Agent 定義檔與其前置讀取清單，僅執行審核並回報問題，不會自動修改正文。*

### 🎨 指令四：呼叫美術總監（任何時機皆可）
**「請呼叫美術總監，為 [角色名/場景描述] 生成視覺概念圖。」**
*AI 將讀取 `Agent_ArtDirector.md`、`Story_Bible.md` 與相關角色檔案，使用 generate_image 工具產出圖片。*

### 📝 指令五：更新進度記憶（章節完成後）
**「請更新 story_progress.md，記錄第 [X] 章的進度摘要。」**
*AI 將依照 `story_progress.md` 中的標準化記憶摘要模板，精煉寫入該章的三項硬性指標。*

### 💾 指令六：提交 Git
**「更新至 Git」 或 「提交存檔」**
*AI 將執行 `git add` 與 `git commit`。未收到此指令前，AI 絕不主動執行任何 Git 操作。*
