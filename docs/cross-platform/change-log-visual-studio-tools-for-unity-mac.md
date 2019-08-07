---
title: 變更記錄檔 (Visual Studio Tools for Unity，Mac) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ff2bcce9e041ff28393020c48563fe345c4fa076
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661824"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>變更記錄檔 (Visual Studio Tools for Unity，Mac)

Visual Studio Tools for Unity 變更記錄。

## <a name="2200"></a>2.2.0.0

2019 年 7 月 25 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **評估：**

  - 已修正 IntPtr 型別的檢閱。

- **偵錯工具：**

  - 已修正捕捉點與函數中斷點的處理方式。

## <a name="2130"></a>2.1.3.0

2019 年 7 月 9 日發行

### <a name="new-features"></a>新功能

- **偵錯工具：**

  - 已新增對捕捉例外狀況子類別的支援。

  - 已新增對 MDS 通訊協定 2.5.1 的支援。

- **整合：**

  - 已新增對 asmdef 檔案的資源。

  - 從範本新增檔案時切換至重新命名模式 (以模擬 Unity 編輯器行為)。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正與 Unity 播放機通訊時，對格式不正確訊息的處理方式。

- **評估：**

  - 已修正運算式中命名空間的處理方式。

## <a name="2120"></a>2.1.2.0

2019 年 7 月 2 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **評估：**

  - 已修正包含非可剖析式運算式的錯誤報告。

## <a name="2110"></a>2.1.1.0

2019 年 6 月 27 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已將 MonoBehaviour API 更新為 2019.1。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正 Unity 專案總管效能。

  - 已修正啟用輕量型組建時輸出的報告警告和錯誤。

  - 已修正輕量型組建效能。

## <a name="2100"></a>2.1.0.0

2019 年 6 月 20 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已停用 Unity 專案的完整建置，改為使用 IntelliSense 錯誤和警告。 事實上，Unity 會使用代表 Unity 內部工作的類別庫專案，建立一個 Visual Studio 方案。 也就是說，當 Unity 的編譯管線遭到關閉時，它永遠不會使用或挑選 Visual Studio 中的組建結果。 在 Visual Studio 中建置只是消耗資源而已。 如果您因為有相依的工具或設定而需要完整建置，您可以停用此最佳化 (設定/Tools for Unity/停用專案的完整建置)。
  
  - 已新增對 UPE 中 Unity 封裝的支援。 只有參考套件 (使用 Packages 資料夾中的 manifest.json) 和本機套件 (內嵌在 Packages 資料夾中) 會顯示。

## <a name="2021"></a>2.0.2.1

2019 年 5 月 30 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增 Unity 執行目標的自訂圖示。

## <a name="2020"></a>2.0.2.0

發行於 2019 年 4 月 2 日

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增在儲存時自動重新整理 Unity 資產資料庫的支援。 這預設會啟用，且在 Visual Studio 中儲存指令碼時，會觸發在 Unity 端的重新編譯。 您可以在 [工具]\\[選項]\\[Tools for Unity]\\[儲存時重新整理 Unity 的 AssetDatabase] 中停用此功能。

  - 新增針對離線文件設定慣用之 Unity 安裝的支援。

  - 新增新編輯器的快顯功能表。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **偵錯工具：**

  - 已修正組件篩選和空白框架的框架檢查。

## <a name="2011"></a>2.0.1.1
 
 發行於 2019 年 3 月 26 日

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 暫時將 Mono 設定為此版本之預設且唯一可用的偵錯工具。

## <a name="2006"></a>2.0.0.6

發行於 2019 年 3 月 26 日

### <a name="new-features"></a>新功能

- **整合：**

  - 新增 [附加至 Unity 並試玩] 的支援。

## <a name="2005"></a>2.0.0.5

發行於 2019 年 3 月 20 日

### <a name="new-features"></a>新功能

- **Project Generation:**

  - 處理解決方案檔案時，保留外部屬性。

## <a name="2004"></a>2.0.0.4

發行於 2019 年 3 月 5 日

### <a name="new-features"></a>新功能

- **整合：**

  - 已更新 ScriptableObject API。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 從範本移除命名空間。

## <a name="2003"></a>2.0.0.3
 
 發行於 2019 年 3 月 5 日

### <a name="new-features"></a>新功能

- **Project Generation:**

  - 公用和序列化欄位將不會再造成警告。 我們已自動隱藏 Unity 專案中建立這些訊息的 CS0649 和 IDE0051 編譯器警告。

- **整合：**

  - 如果有超過一個的 Unity 處理序在執行，系統會提示附加到特定執行個體。

- **評估：**

  - 已新增對區域函式的支援。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **偵錯工具：**

  - 已修正使用舊版通訊協定版本時讀取具名引數上自訂屬性的問題。

## <a name="2002"></a>2.0.0.2

發行於 2019 年 2 月 4 日

### <a name="new-features"></a>新功能

- **整合：**

  - 已更新 MonoBehaviour API。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **偵錯工具：**

  - 已修正偵錯工具中的設定基本值。

## <a name="2001"></a>2.0.0.1

發行於 2018 年 12 月 4 日

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正安裝套件自我內含項目。

## <a name="2000"></a>2.0.0.0
 發行於 2018 年 12 月 4 日

### <a name="new-features"></a>新功能

- **偵錯工具：**

  - 用 Windows 的相同核心 Unity 偵錯工具，取代 Mac 上的 Unity 偵錯工具。

  - 取代 NRefactory 以利將 Roslyn 用於運算式評估。

  - 已新增指標的支援：取值、轉換和指標計算 (此功能需要 Unity 2018.2+ 和新執行階段)。

  - 新增陣列指標檢視 (如在 C++ 中) 的支援。 接受指標運算式然後附加逗號和您要查看之數目的元素。

  - 新增非同步建構的支援。

  - 新增虛擬變數 (例外狀況和物件識別碼) 的支援。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **偵錯工具：**

  - 已修正對格式不正確或不受支援之運算式的運算式評估的問題。

## <a name="1700"></a>1.7.0.0

發行時間：2018 年 11 月 13 日

### <a name="new-features"></a>新功能

- **偵錯工具：**

  - 在 [附加] 對話方塊中新增更多用戶端資訊 (IP、電腦名稱)。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **偵錯工具：**

  - 已修正用於與 Unity 偵錯工具引擎通訊之程式庫中的死結，該死結造成 Visual Studio 或 Unity 凍結，特別是在按下 [附加到 Unity] 或重新啟動遊戲時。

- **整合：**

  - 修正選取其他預設編輯器時的 Unity 外掛程式啟用問題。

  - 修正 Unity 檔案範本建立問題。

## <a name="1602"></a>1.6.0.2

2018 年 7 月 24 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 針對 Unity 已修正的 Unity 效能 Bug 復原因應措施。

## <a name="1601"></a>1.6.0.1

2018 年 7 月 10 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 修正了著色器的程式碼著色支援。

## <a name="1600"></a>1.6.0.0

2018 年 7 月 26 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **精靈：**

  - 修正了 OnApplicationFocus 訊息中的錯字。

- **Project Generation:**

  - Unity 效能 Bug 的暫時性因應措施：在產生專案時，會快取 MonoIslands。

  - 在使用新 Unity 執行階段時，不會再將可攜式 pdb 轉換成 mdb。

## <a name="1502"></a>1.5.0.2

2018 年 4 月 18 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 新增了基本著色器程式碼完成功能的支援。

  - 新增了在切換著色器檔案中切換註解的支援。

## <a name="1501"></a>1.5.0.1

2018 年 3 月 28 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增 Unity 專案總管中額外範本的支援。

## <a name="1500"></a>1.5.0.0

2018 年 3 月 21 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增偵測和附加至透過 USB 所連線 Android Player 的支援。

## <a name="1403"></a>1.4.0.3

2018 年 3 月 5 日發行

### <a name="new-features"></a>新功能

- **Project Generation:**

  - 已新增 Unity 2018.1 中新專案產生器的支援。

- **整合：**

  - 已新增專用設定的選項面板。

## <a name="1402"></a>1.4.0.2

2018 年 1 月 24 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **Project Generation:**

  - 已修正 Mono 版本偵測。

- **整合：**

  - 已修正 2018.1 的時間問題和外掛程式啟用問題。

  - 已修正偵測到新播放器時的通知。

## <a name="1401"></a>1.4.0.1

2018 年 1 月 23 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正按兩下時展開/摺疊資料夾

## <a name="1400"></a>1.4.0.0

2017 年 12 月 13 日發行

### <a name="new-features"></a>新功能

- **Project Generation:**

  - 已新增 .NET Standard 的支援。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 修正自動化 pdb 對 mdb 的偵錯符號轉換。

## <a name="1301"></a>1.3.0.1

2017 年 12 月 12 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正在嘗試變更陣列大小期間，間接呼叫 EditorPrefs.GetBool 對檢查的影響。

- **精靈：**

  - 再插入方法之前先重新整理 Roslyn 內容。

## <a name="1300"></a>1.3.0.0

2017 年 11 月 20 日發行

### <a name="new-features"></a>新功能

- **精靈：**

  - 已新增 [實作 Unity Messages 精靈]。

  - 已新增 VS for Mac 7.4 中新完成 API 的支援。

## <a name="1200"></a>1.2.0.0

2017 年 10 月 23 日發行

### <a name="new-features"></a>新功能

- **偵錯工具：**

  - 已新增可攜式偵錯符號檔的支援。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **Project Generation:**

  - 已修正錯誤新增至組件檔名的額外 .dll 副檔名。

  - 因為預設值現在是 'true'，所以請不要強制執行 AllowAttachedDebuggingOfEditor Unity 旗標。

## <a name="1103"></a>1.1.0.3

2017 年 10 月 23 日發行

### <a name="new-features"></a>新功能

- **Project Generation:**

  - 已新增對 .NET 4.6 設定檔的支援。

## <a name="1102"></a>1.1.0.2

2017 年 8 月 8 日發行

### <a name="new-features"></a>新功能

- **偵錯工具：**

  - 如果不確定要附加的 Unity，請啟動 [附加到處理序] 對話方塊。

- **Project Generation:**

  - 使用 Unity 5.6 時，總是啟用不安全的編譯參數。

## <a name="1101"></a>1.1.0.1

2017 年 7 月 20 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增當地語系化資源的支援。

## <a name="1100"></a>1.1.0.0

2017 年 7 月 12 日發行

### <a name="new-features"></a>新功能

- **整合：**

  - 已新增透過 [附加至處理序] 視窗附加至播放器和編輯器的支援。

- **Project Generation:**

  - 使用 mcs.rsp 檔案修正組件名稱參考。

  - 已新增 assembly.json 編譯單位的支援。

  - 修正具有 API 層級的定義。

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正編譯時的著色器錯誤訊息。

## <a name="1001"></a>1.0.0.1

2017 年 5 月 4 日發行

### <a name="bug-fixes"></a>錯誤 (Bug) 修正

- **整合：**

  - 已修正混合式和一般專案的作用中文件追蹤。

## <a name="1000"></a>1.0.0.0

2017 年 5 月 3 日發行
