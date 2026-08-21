deployment only 
# UGOT: Corebreak Arena

**UGOT: Corebreak Arena** 是一個面向公開玩家的 Godot 4.6.1 展示 Demo。它採用 **2D 假 3D斜俯視** 視覺：玩家操控青色 UGOT，夾取橙色模組並放到青色空位，解除紅色核心的 Sudden Death 鎖定後，以兩次 EMP 終結。

> 遊戲的核心勝負規則完全離線可用。Gemini 任務文案、未來的真機掃描與其他 AI 展示只能作加分層，不能阻礙玩家完成一局，也不會把 API key 放入 Web 版。

## 立即遊玩

| 版本 | 位置 | 使用方式 |
|---|---|---|
| Godot 原始專案 | 本資料夾 | 以 `tools/Godot_v4.6.1-stable_win64.exe` 開啟後按 `F5`，由主選單開始 |
| Windows Demo | `release/win64/UGOT_Corebreak_Arena.exe` | 連同同層 `.pck` 檔保留，直接雙擊 `.exe` |
| Web Demo | `release/web/index.html` | 上傳整個 `release/web/` 資料夾到 itch.io 或靜態網站；不可直接以 `file://` 開啟 |

## 操作與一局流程

| 動作 | 鍵盤／滑鼠 | 手掣 |
|---|---|---|
| 駕駛 UGOT | `WASD` 或方向鍵 | 左搖桿 |
| 衝刺 | `Space` | B |
| 夾取／放置方塊 | `E` | A |
| 掃描 | `Q` | Y |
| 發射 EMP | **左鍵** | RT |

1. 在主選單按「開始遊戲」，閱讀一屏任務簡報。
2. 進入 90 秒碗狀競技場，靠近中央的橙色模組，按 `E` 夾取。
3. 帶它前往青色空位，再按 `E` 放置。
4. HUD 顯示「Sudden Death：已解鎖」後，靠近紅色核心。
5. 使用左鍵／RT 發射兩次 EMP，核心停機即進入結果畫面；結果會顯示完成時間、EMP 命中數和本機排名。

## 已驗證項目

本機的 Godot 4.6.1 已跑完六個單元／整合測試，並已成功建立 Windows 與 Web 發布包。測試涵蓋有效空位判定、解鎖前拒絕核心傷害、回合流程、離線 AI 後備與 2D 假 3D 場景契約。

請勿直接執行裸 `--headless` 命令；標準流程會隔離 `user://`、保留日誌並逐一執行所有 Godot 測試：

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\tools\Run-GodotChecks.ps1 -ProjectRoot .
```

若出現 signal 11，請保留 `tmp\godot_test_user_data\logs\godot_checks.log` 和輸出的重現命令，並將該輪標記為「環境未驗證」。詳情見 [`docs/GODOT_TESTING_ENVIRONMENT.md`](docs/GODOT_TESTING_ENVIRONMENT.md)。

## 生成資產的下一步

請先閱讀 [`docs/DEMO_ASSET_PRODUCTION_PACK.md`](docs/DEMO_ASSET_PRODUCTION_PACK.md)。它列出你可用 Midjourney、MiniMax、ElevenLabs 和 Canva 並行製作的最小資產數量、檔案位置、尺寸、命名、色彩契約和直接可複製的提示詞。生成後只需依檔案名稱放入 `art/` 和 `audio/` 對應資料夾；目前的幾何灰盒則會保證即使美術尚未完成也可演示完整玩法。

玩家畫面流、主選單、任務簡報與碗狀關卡以 [`docs/GAME_DIRECTION.md`](docs/GAME_DIRECTION.md) 為準。完整規則、代理人邊界與比賽日流程請參閱 [`UGOT Arena Kit — 首版正式規格.md`](UGOT%20Arena%20Kit%20%E2%80%94%20%E9%A6%96%E7%89%88%E6%AD%A3%E5%BC%8F%E8%A6%8F%E6%A0%BC.md)、[`AGENTS.md`](AGENTS.md) 和 [`香港 AI Game Jam 2026 — UGOT 比賽日操作手冊.md`](%E9%A6%99%E6%B8%AF%20AI%20Game%20Jam%202026%20%E2%80%94%20UGOT%20%E6%AF%94%E8%B3%BD%E6%97%A5%E6%93%8D%E4%BD%9C%E6%89%8B%E5%86%8A.md)。
