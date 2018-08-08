---
title: 變更記錄檔 (Visual Studio Tools for Unity，Windows) | Microsoft Docs
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: TerryGLee
ms.author: tglee
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 65d78b5b37396572e73928a51f2f215b72dfa311
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381051"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>變更記錄檔 (Visual Studio Tools for Unity，Windows)
Visual Studio Tools for Unity 變更記錄。

## <a name="3701"></a>3.7.0.1
 發行日期：2018 年 5 月 7 日

### <a name="bug-fixes"></a>Bug 修正

-   **安裝程式：**

    -   已修正使用實驗性組建時的相依性問題。

## <a name="3700"></a>3.7.0.0
 發行日期：2018 年 5 月 7 日

### <a name="new-features"></a>新功能

-   **偵錯：**

    -   已新增對協調偵錯的支援 (使用同一個 Visual Studio 工作階段對多個播放器/編輯器進行偵錯)。
    
    -   已新增對 Android USB 播放器偵錯的支援。
    
    -   已新增對 UWP/IL2CPP 播放器偵錯的支援。

-   **評估：**

    -   已新增對十六進位指定名稱的支援。
    
    -   已改善監看視窗評估體驗。

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   修正例外狀況設定的使用方式。

-   **Project Generation:**

    -   產生時排除套件管理員編譯單位。

## <a name="3605"></a>3.6.0.5
 發行日期：2018 年 3 月 13 日

### <a name="new-features"></a>新功能

-   **Project Generation:**

    -   已新增 Unity 2018.1 中新專案產生器的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   已修正處理自訂專案的損毀狀態。

-   **偵錯工具：**

    -   已修正設定下一個陳述式。

## <a name="3604"></a>3.6.0.4
 發行日期：2018 年 3 月 5 日

### <a name="bug-fixes"></a>Bug 修正

-   **Project Generation:**

    -   已修正 Mono 版本偵測。

-   **整合：**

    -   已修正 2018.1 的時間問題和外掛程式啟用問題。

## <a name="3603"></a>3.6.0.3
 發行日期：2018 年 2 月 23 日

### <a name="new-features"></a>新功能

-   **Project Generation:**

    -   已新增 .NET Standard 的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **Project Generation:**

    -   已修正 Unity 目標架構偵測。

-   **偵錯工具：**

    -   已修正在 Usercode 外擲回例外狀況的中斷問題。

## <a name="3602"></a>3.6.0.2
 發行日期：2018 年 2 月 7 日

### <a name="new-features"></a>新功能

-   **整合：**

    -   更新 2017.3 的 UnityMessage API 介面。

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   只針對外部變更重新載入專案 (搭配節流)。

## <a name="3601"></a>3.6.0.1
 發行日期：2018 年 1 月 24 日

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   修正自動化 pdb 對 mdb 的偵錯符號轉換。

    -   已修正在嘗試變更陣列大小期間，間接呼叫 EditorPrefs.GetBool 對檢查的影響。

## <a name="3600"></a>3.6.0.0
 發行日期：2018 年 1 月 10 日

### <a name="new-features"></a>新功能

-   **Project Generation:**

    -   新增對 2018.1 MonoIsland 參考模型的支援。

-   **評估：**

    -   新增對 $exception 識別碼的支援。

-   **偵錯工具：**

    -   新增對搭配新 Unity 執行階段的 DebuggerHidden/DebuggerStepThrough 屬性的支援。

-   **精靈：**

    -   導入針對精靈的「最新」版本。

### <a name="bug-fixes"></a>Bug 修正

-   **Project Generation:**

    -   已修正播放程式專案的專案指引計算。

-   **偵錯工具：**

    -   已修正處理中斷事件的競爭。

-   **精靈：**

    -   再插入方法之前先重新整理 Roslyn 內容。

## <a name="3503"></a>3.5.0.3
 發行日期：2018 年 1 月 9 日

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   修正自動化 pdb 對 mdb 的偵錯符號轉換。

## <a name="3502"></a>3.5.0.2
 發行日期：2017-12-04

### <a name="new-features"></a>新功能

-   **整合：**

    -   Unity 專案現在會在您從 Unity 新增或移除指令碼時，自動重新載入 Visual Studio 中。

-   **偵錯工具：**

    -   已新增選項，使用 Xamarin 和 Visual Studio for Mac 共用的單聲道偵錯工具偵錯 Unity 編輯器。

    -   已新增可攜式偵錯符號檔的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **整合：**

    -   已修正安裝相依性問題。

    -   已修正 Unity API 說明功能表未顯示。

-   **Project Generation:**

    -   已修正使用 IL2CPP/.NET 4.6 後端處理 UWP 遊戲時產生播放程式專案的問題。

    -   已修正錯誤新增至組件檔名的額外 .dll 副檔名。

    -   已修正特定專案 API 相容性層級的使用，而非全域專案 API 相容性層級。

    -   因為預設值現在是 'true'，所以請不要強制執行 AllowAttachedDebuggingOfEditor Unity 旗標。

## <a name="3402"></a>3.4.0.2
 發行日期：2017 年 9 月 19 日

### <a name="new-features"></a>新功能

-   **Project Generation:**

    -   已新增 assembly.json 編譯單位的支援。

    -   停止將 Unity 組件複製至專案資料夾。

-   **偵錯工具：**

    -   已新增使用新 Unity 執行階段設定下一個陳述式的支援。

    -   已新增使用新 Unity 執行階段之 Decimal 類型的支援。

    -   已新增隱含/明確轉換的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **評估：**

    -   修正具有隱含大小的陣列建立。

    -   修正具有區域變數的編譯器所產生項目。

-   **Project Generation:**

    -   修正 4.6 API 層級的 Microsoft.CSharp 參考。

## <a name="3302"></a>3.3.0.2
 發行日期：2017 年 8 月 15 日

### <a name="bug-fixes"></a>Bug 修正

-   **Project Generation:**

    -   已修正 Unity 5.5 和舊版本上 Visual Studio 解決方案的產生。

## <a name="3300"></a>3.3.0.0
 發行日期：2017 年 8 月 14 日

### <a name="new-features"></a>新功能

-   **評估：**

    -   已新增使用新 Unity 執行階段建立結構的支援。

    -   已新增指標的極簡支援。

### <a name="bug-fixes"></a>Bug 修正

-   **評估：**

    -   修正基本物件的方法引動過程。

    -   修正標有 BeforeFieldInit 之類型的欄位評估。

    -   修正具有二元運算子 (減法) 的非支援呼叫。

    -   修正將項目新增至 Visual Studio Watch 時的問題。

-   **Project Generation:**

    -   使用 mcs.rsp 檔案修正組件名稱參考。

    -   修正具有 API 層級的定義。

## <a name="3200"></a>3.2.0.0
 發行日期：2017 年 5 月 10 日

### <a name="new-features"></a>新功能

-   **安裝程式：**

    -   已新增清除 MEF 快取的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **程式碼編輯器：**

    -   修正具有自訂屬性的分類/完成。

    -   修正 Unity 訊息的閃爍。

## <a name="3100"></a>3.1.0.0
 發行日期：2017 年 4 月 7 日

### <a name="new-features"></a>新功能

-   **偵錯工具：**

    -   已新增對全新 Unity 執行階段的支援 (以及 .NET 4.6 / C# 6 相容性)。

-   **Project Generation:**

    -   已新增對 .NET 4.6 設定檔的支援。

    -   已新增對 mcs.rsp 檔案的支援。

    -   使用 Unity 5.6 時，總是啟用不安全的編譯參數。

    -   已新增在使用 Windows 市集平台和 il2cpp 後端時對 "Player" 專案產生的支援。

### <a name="bug-fixes"></a>Bug 修正

-   **程式碼編輯器：**

    -   使用自動完成來插入方法之後的固定插入號位置。

-   **Project Generation:**

    -   已移除組件版本的後續處理步驟。

## <a name="3001"></a>3.0.0.1
 發行日期：2017 年 3 月 7 日

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>此版本包括 2.8.x 系列開始導入的所有新功能和錯誤修正。

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 Preview 3
 發行日期：2017 年 1 月 25 日

### <a name="bug-fixes"></a>Bug 修正

-   **專案產生：**

    -   已修正參考了外掛程式專案兩次的迴歸，第一次是將其當成二進位 DLL，接著則是當成專案參考。

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 Preview 2
 發行日期：2017 年 1 月 23 日

### <a name="bug-fixes"></a>Bug 修正

-   **程式碼編輯器：**

    -   已修正在完成啟動未加上大括號的屬性宣告時所發生的當機。

-   **偵錯工具：**

    -   已修正在新的 Unity 編譯器/執行階段下方使用協同程式的函式中斷點。

    -   已新增 (在找不到對應的來源位置時) 發生無法繫結之中斷點的警告。

-   **Project Generation:**

    -   已修正使用特殊/當地語系化的字元產生 csproj。

    -   已修正資產以外的來源，例如程式庫 (像是 Facebook SDK)。

-   **其他：**

    -   已新增檢查，可防止 Unity 在安裝或解除安裝時執行。

    -   已切換至 https，以將目標設為遠端 Unity 文件。

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 Preview
 發行日期：2016 年 11 月 17 日

### <a name="new-features"></a>新功能

-   **一般：**

    -   已新增 Visual Studio 2017 安裝程式支援。

    -   已新增 Visual Studio 2017 擴充功能支援。

    -   已新增當地語系化支援。

-   **程式碼編輯器：**

    -   已新增適用於 Unity 訊息的 C# IntelliSense。

    -   已新增適用於 Unity 訊息的 C# 程式碼色彩。

-   **偵錯工具：**

    -   已新增 `is`、`as`、直接轉型、`default`、`new` 運算式的支援。

    -   已新增 string concat 運算式的支援。

    -   已新增以十六進位顯示整數值的支援。

    -   已新增建立新的暫存變數 (陳述式) 的支援。

    -   已新增隱含基本轉換的支援。

    -   已新增可在預期或找不到某個類型時提供的更好錯誤訊息。

-   **Project Generation:**

    -   已從專案名稱中移除 CSharp 尾碼。

    -   已移除全系統 msbuild 目標檔案的參考。

-   **精靈：**

    -   已新增在非行為類型中 (例如 Editor 或 EditorWindow) 對 Unity 訊息的支援。

    -   已切換至 Roslyn，以插入並格式化 Unity 訊息。

### <a name="bug-fixes"></a>Bug 修正

-   **偵錯工具：**

    -   已修正在評估泛型類型時損毀 Unity 的 Bug。

    -   已修正可為 Null 的類型的處理方式。

    -   已修正列舉的處理方式。

    -   已修正巢狀成員類型的處理方式。

    -   已修正集合索引子存取。

    -   已修正使用新的 C# 編譯器偵錯迭代器框架的支援。

-   **Project Generation:**

    -   已修正在以 Unity Web Player 為目標時無法編譯的 Bug。

    -   已修正在搭配 Web 編譯的檔案名稱編譯指令碼時無法編譯的 Bug。

## <a name="2300"></a>2.3.0.0
 發行日期：2016 年 7 月 14 日

### <a name="new-features"></a>新功能

-   **一般：**

    -   已在 Visual Studio 錯誤清單中新增一個選項來停用 Unity 主控台記錄。

    -   已新增一個選項來修改所產生的專案屬性。

-   **偵錯工具：**

    -   已新增文字、XML、HTML 和 JSON 字串視覺化檢視。

-   **精靈：**

    -   已新增遺漏的 MonoBehaviors。

### <a name="bug-fixes"></a>Bug 修正

-   **一般：**

    -   已修正與 ReSharper 的衝突，這使得 Visual Studio 內的控制項不會顯示。

    -   已修正與 Xamarin 的衝突，這在某些情況下會導致無法進行偵錯。

-   **偵錯工具：**

    -   已修正偵錯時造成 Visual Studio 凍結的問題。

    -   已修正 Visual Studio 2015 中的函式中斷點問題。

    -   已修正數個運算式評估問題。

## <a name="2200"></a>2.2.0.0
 發行日期：2016 年 2 月 4 日

### <a name="new-features"></a>新功能

-   **精靈：**

    -   在 [實作 MonoBehavior 精靈]  中新增了智慧型搜尋。

    -   使精靈感知內容；例如，只有處理 NetworkBehavior 時才提供 NetworkBehavior 訊息。

    -   在精靈中新增了對 NetworkBehavior 訊息的支援。

-   **UI：**

    -   已新增設定 MonoBehavior 訊息可見性的選項。

    -   已移除與 Unity 專案無關的 Visual Studio 屬性頁。

### <a name="bug-fixes"></a>Bug 修正

-   **專案產生：**

    -   已修正 Unity 4.6 上 UnityEngine 和 UnityEditor 的參考。

    -   已修正 Unity 在 OSX 上執行時的專案檔產生。

    -   已修正含有 # 字元之專案名稱的處理。

    -   已將產生的專案限制為 C# 4。

-   **偵錯工具：**

    -   已修正在 Unity 共常式內偵錯時的運算式評估問題。

    -   已修正偵錯時造成 Visual Studio 凍結的問題。

-   **UI：**

    -   已修正與 [Tabs Studio](https://tabsstudio.com/) Visual Studio 擴充功能不相容的問題。

-   **安裝程式：**

    -   藉由建立 HKLM 登錄項目來支援 VSTU 的全機器安裝 (針對所有使用者安裝)。

    -   已修正針對多個不同版本的 Visual Studio 安裝同一個版本的 VSTU 時，解除安裝 VSTU 的問題。 例如，同時安裝 VSTU **2015** 2.1.0.0 和 VSTU **2013** 2.1.0.0 時。

## <a name="2100"></a>2.1.0.0
 發行日期：2015 年 9 月 8 日

### <a name="new-features"></a>新功能

-   Unity 5.2 支援

### <a name="bug-fixes"></a>Bug 修正

-   在 Unity < 4.2 顯示功能表項目

-   當 Visual Studio 鎖定 XML Intellisense 檔案時，不再顯示錯誤訊息。

-   當條件式引數不是布林值時，處理 <\<變更時>> 條件中斷點。

-   已修正 Windows 市集 App 之 UnityEngine 和 UnityEditor 組件的參考。

-   已修正當偵錯工具逐步執行時的錯誤：無法逐步執行，一般例外狀況。

-   已修正在 Visual Studio 2015 的叫用次數中斷點。

## <a name="2000"></a>2.0.0.0
 發行日期：2015 年 7 月 20 日

### <a name="bug-fixes"></a>Bug 修正

-   **Unity 整合：**

    -   已修正匯入 DLL 和其偵錯符號 (PDB) 時以 Visual Studio 2015 建立的偵錯符號轉換。

    -   匯入 DLL 和其偵錯符號 (PDB) 時一律產生 MDB 檔案，但若同時提供 MDB 檔則除外。

    -   已修正 Unity 專案目錄受 obj 目錄干擾的問題。

    -   已修正 System.Xml.Link 和 System.Runtime.Serialization 參考產生。

    -   已加入專案檔案產生應用程式開發介面攔截的多個訂閱者支援。

    -   一定要完成專案檔案產生，即使其中一個要產生的檔案已被鎖定。

    -   已加入在指定要包含在 C# 專案中的檔案時，延伸模組篩選器中的 * 萬用字元支援。

-   **Visual Studio 整合：**

    -   已修正 Productivity Power Tools 相容性問題。

    -   已修正產生 MonoBehaviors 事件與委派的宣告。

-   **偵錯工具：**

    -   已修正偵錯時的潛在凍結。

    -   已修正 [區域變數] 在某些堆疊框架中可能不會顯示區域變數的問題。

    -   已修正空白陣列的檢查。

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 Preview 2
 發行日期：2015 年 4 月 2 日

### <a name="new-features"></a>新功能

-   **Unity Project Explorer：**

    -   在 Unity Project Explorer 中重新命名檔案時自動重新命名類別 (請參閱 [選項]  對話方塊)。

    -   在 Unity Project Explorer 中自動選取新建立的指令碼。

    -   在 Unity Project Explore 中追蹤作用中的指令碼 (請參閱 [選項]  對話方塊)。

    -   雙重同步處理 Visual Studio 方案總管 (請參閱 [選項]  對話方塊)。

    -   在 Unity Project Explorer 中採用 Visual Studio 圖示。

-   **偵錯工具：**

    -   從已儲存或最近使用的偵錯目標清單中選取作用中的偵錯目標 (請參閱 [選項]  對話方塊)。

    -   在 MonoBehavior 方法上建立函式中斷點，並套用至多個 MonoBehavior 類別。

    -   在偵錯工具中支援 [設定物件 ID]。

    -   在偵錯工具中援中斷點遇到次數。

    -   在偵錯工具中支援發生例外狀況時中斷 (實驗性質， 請參閱 [選項]  對話方塊)。

    -   在偵錯工具中評估運算式時，支援建立物件和陣列。

    -   在偵錯工具中評估運算式時，支援 Null 比較。

    -   在偵錯工具監看式視窗中，篩選掉過時的成員。

-   **安裝程式：**

    -   最佳化 Visual Studio Tools for Unity 擴充功能註冊。

    -   安裝 Unity 5 的 Visual Studio Tools for Unity 套件。

-   **文件：** 提升文件產生的效能。

-   **精靈：** 支援 Unity 4.6 和 Unity 5 的新 MonoBehavior 方法。

-   **Unity：** 在專案檔產生期間，查閱 .rsp 檔中的不安全旗標和自訂定義。

-   **UI：** 在 Visual Studio 中新增 Visual Studio Tools for Unity [選項]  對話方塊。

### <a name="bug-fixes"></a>Bug 修正

-   **Unity Project Explorer：**

    -   從 Visual Studio 方案總管移動或重新命名檔案之後，重新整理 Unity Project Explorer。

    -   在 Unity Project Explorer 中重新命名檔案時，保留選取項目。

    -   避免在 Unity Project Explorer 中按兩下檔案時自動展開和摺疊。

    -   確保在 Unity Project Explorer 中能看到新選取的檔案。

-   **偵錯工具：**

    -   避免在偵錯工具中評估運算式時 Visual Studio 可能凍結。

    -   確保方法引動過程發生在偵錯工具的適當網域上。

-   **Unity：**

    -   更正 Unity 5 的 UnityVS.OpenFile 位置。

    -   更正 Unity 5 的 pdb2mdb 位置。

    -   避免專案檔案產生期間可能的例外狀況。

    -   避免在 OSX 上執行 Unity 時可能凍結。

    -   處理內部例外狀況。

    -   將 Unity 主控台記錄傳送至 VS 錯誤清單。

-   **文件：** 更正新 Unity 文件的文件產生。

-   **專案：** 視需要移動及重新命名 Unity .meta 檔，即使在資料夾中亦然。

-   **精靈：** 更正產生程式碼時的 MonoBehavior 方法參數順序。

-   **UI：** 內容功能表和圖示支援 Visual Studio 佈景主題。

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 Preview
 發行日期：2014 年 11 月 12 日

### <a name="new-features"></a>新功能

-   支援 Visual Studio 2015。

-   Visual Studio 2015 之 Unity 著色器的程式碼著色。

-   偵錯時視覺化值的方式已改進：

    -   改進 ArrayLists、Lists、Hashtables 和 Dictionaries 的視覺效果。

    -   將非共用成員和靜態成員顯示為監看式和本機檢視中的分類。

    -   改進 Unity SerializedProperty 的顯示，只評估值欄位對該屬性是否有效。

    -   類別和結構的 DebuggerDisplayAttribute 支援。

    -   DebuggerTypeProxyAttribute 支援。

-   使用精靈插入 MonoBehaviour 方法遵循使用者程式碼撰寫慣例。

-   在 UnityVS 產生的專案中實作編譯時期文字範本的支援。

-   在 UnityVS 產生的專案中實作 ResX 資源的支援。

-   支援從 Unity 開啟 Visual Studio 中的著色器。

### <a name="bug-fixes"></a>Bug 修正

-   在 Visual Studio 中觸發附加並播放之後，於 Unity 中啟動遊戲之前清除通訊端。 這會修正使用附加並播放時，Unity 和 VS 之間的一些連接穩定性問題。

-   避免呼叫 Unity 指令碼引擎偵錯工具介面中容易凍結 Unity 的方法。 這會修正附加偵錯工具時的 Unity 凍結問題。

-   修正沒有符號時顯示呼叫堆疊的作業。

-   如果沒有必要，請不要註冊記錄回呼。

## <a name="1920"></a>1.9.2.0
 發行日期：2014 年 10 月 9 日

### <a name="new-features"></a>新功能

-   改進 Unity 播放器的偵測。

-   使用檔案開啟工具時，使 Unity 傳遞行號及檔案名稱。

-   如果沒有本機文件，預設會是線上 Unity 文件。

### <a name="bug-fixes"></a>Bug 修正

-   修正網域重新載入之後遇到中斷點時，可能發生的 Unity 損毀。

-   修正網域重新載入之後關閉 [組態] 或 [關於] 視窗時，Unity 主控台中所顯示的例外狀況。

-   修正在本機執行之 64 位元 Unity 的偵測。

-   修正每個 Unity 版本精靈中的 MonoBehaviours 篩選。

-   修正副檔名篩選是空的時，便在專案檔中包含所有資產的 Bug。

## <a name="1910"></a>1.9.1.0
 發行日期：2014 年 9 月 22 日

### <a name="new-features"></a>新功能

-   最佳化將中斷點繫結至來源位置的作業。

-   在偵錯工具的運算式評估中支援多載方法。

-   在偵錯工具的運算式評估中支援以 Boxing 處理基本和實值類型。

-   支援在偵錯匿名方法時，重新建立 C# 區域變數環境。

-   從 Visual Studio 刪除或重新命名檔案時，會刪除並重新命名 .meta 檔。

### <a name="bug-fixes"></a>Bug 修正

-   修正 Visual Studio 佈景主題的處理。 之前，黑色佈景主題的對話方塊可能會顯示為空白 (連接問題 [#932637](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/932637/) 和 [#936439](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/936439/))。

-   修正將偵錯工具連接到正在重新編譯的 Unity 時的 Unity 凍結問題 (連接問題 [#947119](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/947119/) 和 [#969211](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/969211/))。

-   修正對其他系統上所編譯的遠端編輯器或播放器進行偵錯時的中斷點問題。

-   修正遇到中斷點時，可能發生的 Visual Studio 損毀。

-   修正中斷點繫結，以避免中斷點顯示為已卸載。

-   修正偵錯工具中的變數範圍處理，以避免即時變數超出範圍。

-   修正偵錯工具之運算式評估中的靜態成員查閱 (連接問題 [#953379](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/953379/))。

-   修正偵錯工具之運算式評估中的類型顯示，以顯示靜態欄位和屬性。

-   修正 Unity 專案名稱包含 Visual Studio 禁止的特殊字元時的方案產生 (連接問題 #948666)。

-   修正 Visual Studio Tools Unity 套件，以在取消核取選項之後立即停止傳送主控台事件 (連接問題 #933357)。

-   修正參考的偵測，以適當地重新產生新應用程式開發介面的參考 (例如 UnityVS 所產生之專案中的 UnityEngine.UI)。

-   修正安裝程式，要求在安裝前關閉 Visual Studio，以避免損毀安裝。

-   修正安裝程式，以將 Unity 參考組件安裝為可在所有 VSTU 版本之間共用的適當獨立元件。

-   修正在 64 位元版本的 Unity 中使用 VSTU 開啟指令碼的作業。

## <a name="1900"></a>1.9.0.0
 發行日期：2014 年 7 月 29 日

### <a name="new-features"></a>新功能

-   在 [附加 Unity 偵錯工具] 視窗中，新增輸入要偵錯之自訂 IP 和通訊埠的功能。

-   新增組態選項，以設定 Unity 是否要在背景執行。

-   新增組態選項，以產生方案和專案檔，或只產生專案檔。

-   啟動目標：選擇附加至 Unity，或附加至 Unity 並播放。

-   在偵錯工具中顯示多維陣列。

-   處理新的 Unity 播放器偵錯通訊埠。

-   處理新 Unity 組件 (例如 Unity 4.6 GUI 組件) 的參考。

-   偵錯時，解構關閉以適當地顯示區域變數。

-   偵錯時，將產生的迭代器變數解構為引數。

-   專案重新載入之後，保留 Unity Project Explorer 的狀態。

-   新增命令，以同步處理 Unity Project Explorer 與目前文件。

### <a name="bug-fixes"></a>Bug 修正

-   修正條件式中斷點，其條件會在啟動偵錯工具之前設定。

-   修正 UnityEngine 的參考，以避免出現警告。

-   修正剖析 Unity Beta 版的作業。

-   修正遇到中斷點或逐步偵錯時，區域變數視窗中未顯示變數的問題。

-   修正 Visual Studio 2013 中的變數工具提示。

-   修正針對 Unity 4.5 產生 IntelliSense 文件的作業。

-   修正網域重新載入之後的 Unity / Visual Studio 通訊 (Unity 中的播放/停止)。

-   修正 Visual Studio 佈景主題一部分的處理。

> [!IMPORTANT]
>  C# 一直是 Unity 生態系統的主流語言 (新範例資產使用 C#、Unity 文件預設為 C#)，我們移除了對 UnityScript 和 Boo 的基本支援，以改進將焦點放在 C# 的體驗。 因此，VSTU 方案現在只使用 C#，載入更快。

## <a name="1820"></a>1.8.2.0
 發行日期：2014 年 1 月 7 日

### <a name="new-features"></a>新功能

-   解決遠端探索編輯器時，Mavericks 上的 Unity 指令碼引擎的網路層級問題。

-   處理新的通訊埠，以探索遠端 Unity 播放器。

-   參考目前組建目標特有的 UnityEngine 組件。

-   新增設定，以篩選要加入所產生之專案的檔案。

-   新增設定，以停用將主控台記錄傳送至 Visual Studio 錯誤清單。 如果您使用 PlayMaker 或 Console Pro，這會很有用，因為 Unity 中只會註冊一個回呼來接收主控台記錄。

-   新增設定，以停用 mdb 偵錯符號的產生。 如果您要自行產生 mdb，這會很有用。

### <a name="bug-fixes"></a>Bug 修正

-   修正在 VS 中開啟 Unity >= 4.2 的檔案會失去 IntelliSense 時的回復。

-   修正處理自訂佈景主題的 VS 對話方塊。

-   修正關閉 UPE 內容功能表的作業。

-   避免特定版本產生的組件不同步時所發生的 Unity 損毀。

## <a name="1810"></a>1.8.1.0
 發行日期：2013 年 11 月 21 日

### <a name="new-features"></a>新功能

-   調整 Unity 4.3 應用程式開發介面的 MonoBehaviour 精靈。

-   MonoBehaviour 精靈會根據您所使用的版本來篩選 Unity 應用程式開發介面。

-   Unity > 4.1 的專案新增 System.Xml.Linq 參考。

-   修飾 Debug.Log 的呼叫，不包含訊息中的 StackTrace 開頭。

### <a name="bug-fixes"></a>Bug 修正

-   修正我們可能對 Visual Studio 中 JavaScript 檔案的預設處理造成干擾的 Bug。

-   確實修正出現在 VS 中的白色像素。

-   修正 SCM 將 UnityVS.VersionSpecific 組件標示為唯讀時對組件的偵測。

-   修正在 UnityVS 套件中建立通訊端時的例外狀況。

-   修正從 Visual Studio 組件載入內建影像時所發生的 Visual Studio 損毀。

-   修正為 Unity 的來源組建產生 UnityVS.VersionSpecific 時的 Bug。

-   修正在 Unity 套件中開啟通訊端時可能的凍結問題。

-   修正其名稱含有破折號 (-) 之 Unity 專案的處理。

-   修正從 Unity 開啟指令碼不會與 Unity 4.2 (含) 以後版本的 ALT+TAB 鍵順序混淆。

## <a name="1800"></a>1.8.0.0
 發行日期：2013 年 9 月 24 日

### <a name="new-features"></a>新功能

-   大幅改進偵錯工具連接速度。

-   自動處理在 Unity 4.2 (含) 以後版本中巡覽至檔案和行的作業。

-   條件式中斷點。

-   專案檔產生器現在會處理 T4 範本。

-   使用新的應用程式開發介面來更新 MonBehavior 精靈。

-   以 C# 撰寫的 IntelliSense 文件，適用於 Unity 類型。

-   算術和邏輯運算式評估。

-   改進遠端偵錯預覽的遠端編輯器探索。

### <a name="bug-fixes"></a>Bug 修正

-   修正中斷連接偵錯工具之後，VS 中的執行緒可能會遺漏的 Bug。

-   修正出現在 VS 中的白色像素。

-   修正按一下狀態列圖示的處理。

-   修正產生含有 [Plugins] 資料夾中組件之參考的作業。

-   修正發生例外狀況時，從 UnityVS 套件建立通訊端的作業。

-   修正新版 UnityVS 的偵測。

-   修正授權到期時的授權管理員提示。

-   修正將偵錯工具附加至 VS 的處理序視窗時，可能呈現空白處理序清單的 Bug。

-   修正在本機檢視中變更布林值的作業。

## <a name="1220"></a>1.2.2.0
 發行日期：2013 年 7 月 9 日

### <a name="bug-fixes"></a>Bug 修正

-   處理運算式評估工具中的完整名稱。

-   修正與例外狀況處理相關的凍結問題，其中 Unity 指令碼引擎會將不正確的 StackFrame 資料傳送給我們。

-   修正 Web 目標的建置流程。

-   修正啟動 Visual Studio 時可能發生的錯誤，以及啟動時，要開啟的檔案清單中出現已刪除之檔案的錯誤。

-   修正 UnityVS.OpenFile 以處理非指令碼檔案，例如編譯的著色器。

-   我們現在會參考所有 C# 專案中的 Boo.Lang 和 UnityScript.Lang。

-   修正專案具有特殊字元時，在專案中產生參考的作業。

-   解決 VS 問題，其中對已處置的專案呼叫方法會觸發多個 NullReferenceException MessageBox。

-   修正 Unity 4.2 Beta 組件的處理。

## <a name="1210"></a>1.2.1.0
 發行日期：2013 年 4 月 9 日

### <a name="bug-fixes"></a>Bug 修正

-   針對發生 IO 錯誤時的程式碼完成 (例如唯讀檔案或 Visual Studio 鎖定的檔案)，修正 Unity 組件的本機部署。

-   修正從 Unity 開啟 Visual Studio 中已開啟的指令碼時，無法將焦點放在檔案的回復。

-   修正新例外狀況處理的效能問題。

-   修正某些外部 DLL 中的中斷點繫結。

## <a name="1200"></a>1.2.0.0
 發行日期：2013 年 3 月 25 日

### <a name="new-features"></a>新功能

-   大幅改進偵錯工具連接速度。

-   針對大型專案最佳化 Unity Project Explorer。

-   允許在發生已處理和未處理的例外狀況時中斷 (或不中斷) 的 Visual Studio 設定。

-   允許對區域變數呼叫 ToString 的 Visual Studio 設定。

-   新增功能表 [偵錯] -> [附加 Unity 偵錯工具]，可用來偵錯 Unity 播放器。

-   保留產生方案檔時加入 UnityVS 方案的自訂專案。

-   新增鍵盤快速鍵 CTRL+ALT+M -> CTRL+H，以顯示插入號位置處之 Unity 函式或成員的 Unity 文件。

-   從 Visual Studio 編譯時將編譯器回應檔 (rsp) 列入考量。

-   偵錯產生器方法時，解構編譯器產生的類型以顯示變數。

-   簡化遠端偵錯，不再需要設定 Unity 的共用資料夾。 現在您只需要具有從 Windows 存取 Unity 專案的權限即可。

-   將自訂 Unity 設定檔安裝為標準 .NET 目標設定檔。 這會修正 ReSharper 可能顯示的所有誤判。

-   解決 Unity 指令碼引擎 Bug，讓偵錯工具不會在未適當註冊的執行緒上中斷。

-   重新設計檔案開啟工具，以避免在 VS 中發生競爭的情況 (其聲稱能夠開啟檔案，但在提出檔案開啟要求時卻損毀)。

-   UnityVS 現在會在 VS 建置專案時要求重新整理組建，而不是在儲存檔案時。

### <a name="bug-fixes"></a>Bug 修正

-   修正我們的自訂 .NET 設定檔

-   修正主題設定整合，這會修正 VS 2012 暗色調佈景主題的問題。

-   修正 VS 2012 中的快速行為快速鍵。

-   修正偵錯且非主要執行緒遇到中斷點時，可能發生的逐步偵錯問題。

-   修正類型別名 (例如 int) 的 UnityScript 和 Boo 完成。

-   修正撰寫新的 UnityScript 或 Boo 字串時的例外狀況。

-   修正無法載入方案時，Unity 功能表中的例外狀況。

-   修正 Bug UVS-48：輸入雙引號有時會產生錯誤並中斷所有函式 (程式碼完成、語法反白顯示等)。

-   已修正 Bug UVS-46：按一下 Visual Studio 的 [錯誤清單] 時，重複開啟指令碼檔案 (UnityScript)。

-   已修正 Bug UVS-42：狀態列中的 Unity 連線標誌不會處理 VS 2012 中的滑鼠事件。

-   已修正 Bug UVS-44：VS 2012 中未提供代表 Quick MonoBehaviours 的 CTRL+SHIFT+Q。

-   已修正 Bug UVS-40：當視窗在 VS2012 的「暗色調」佈景主題中沒有作用時，無法讀取 Unity Project Explorer 中的選取項目。

-   已修正 Bug UVS-39：Token 化逸出字串的問題。

-   已修正 Bug UVS-35：檢查變數時會對物件叫 ToString。

-   已修正 Bug UVS-27：Goto 符號視窗與 VS2012 的「暗色調」佈景主題不一致。

-   已修正 Bug UVS-11：協同程式中的區域變數。

## <a name="1100---beta-release"></a>1.1.0.0 - 搶鮮版 (Beta)
 發行日期：2014 年 10 月 9 日

## <a name="10130"></a>1.0.13.0
 發行日期：2013 年 1 月 21 日

### <a name="bug-fixes"></a>Bug 修正

-   修正目標偵錯項目傳送無效的執行緒事件時，可能發生的 Visual Studio 鎖定。 通常會在偵錯 OSX 上的遠端 Unity 時發生。

-   修正例外狀況關閉偵錯工具時，可能發生的 Visual Studio 鎖定。

-   修正命名空間中有 C# MonoBehavior 時的 MonoBehavior 協助程式問題。

-   修正 Visual Studio 2012 中 UnityScript 的偵錯工具提示。

-   修正只從 Unity 變更偵錯常數時的專案產生。

-   修正 Unity Project Explorer 中的鍵盤巡覽。

-   修正逸出字串的 UnityScript 顏色標示。

-   修正我們的檔案開啟工具，以更容易猜到在 Unity 外部使用時的專案名稱。 當使用者在 Unity 中使用委派給 UnityVS 的協力廠商檔案開啟工具時，便需要這項修正。

-   修正從 Unity 傳送至 UnityVS 的長訊息處理。 之前，長訊息可能會損毀 UnityVS 的傳訊部分。 因此，UnityVS 有時不會從 Unity 開啟檔案。

## <a name="10120"></a>1.0.12.0
 發行日期：2013 年 1 月 3 日

### <a name="bug-fixes"></a>Bug 修正

-   修正 Visual Studio 刪除中斷點時，可能發生的 Visual Studio 鎖定。

-   修正 Unity 重新編譯遊戲指令碼之後不會遇到一些中斷點的 Bug。

-   修正偵錯工具，以在中斷點解除繫結時適當地通知 Visual Studio。

-   修正可能防止 Visual Studio 偵錯工具偵錯原生程式的註冊問題。

-   修正評估 UnityScript 和 Boo 運算式時可能發生的例外狀況。

-   修正變更 Unity 中的 .NET 應用程式開發介面層級不會觸發專案檔更新的回復。

-   修正使用者程式碼無法參與記錄回呼處理常式的應用程式開發介面問題。

## <a name="10110"></a>1.0.11.0
 發行日期：2012 年 11 月 28 日

### <a name="new-features"></a>新功能

-   Unity 4 的官方支援。

-   從 Unity Project Explorer 操作指令碼。

-   Visual Studio [巡覽至] 視窗中的整合。

-   剖析資訊主控台訊息，以在按一下 [錯誤清單] 時，前往第一個含有符號的 StackFrame。

-   新增 [應用程式開發介面](../cross-platform/customize-project-files-created-by-vstu.md) ，讓使用者參與專案產生。

-   新增 [應用程式開發介面](../cross-platform/share-the-unity-log-callback-with-vstu.md) ，讓使用者參與 LogCallback。

### <a name="bug-fixes"></a>Bug 修正

-   修正 Visual Studio 2012 中 Unity Project Explorer 的背景回復。

-   修正為完整 .NET 設定檔的使用者產生專案的作業。

-   修正為 Web 目標的使用者產生專案的作業。

-   修正專案產生，以包含 Unity 所使用的 DEBUG 和 TRACE 編譯符號。

-   修正在我們的 Goto 符號視窗中使用特殊字元時發生損毀的問題。

-   修正無法在 Visual Studio 的狀態列中插入圖示時發生損毀的問題。

## <a name="10100"></a>1.0.10.0
 發行日期：2012 年 10 月 9 日

### <a name="bug-fixes"></a>Bug 修正

-   修正 Visual Studio 2010 中 Unity Project Explorer 的背景。

-   修正 UnityVS 嘗試將偵錯工具附加至其偵錯工具介面之前已損毀的 Unity 時，可能發生的 Visual Studio 凍結。

-   修正設定中斷點並發生 AppDomain 重新載入時，可能發生的 Visual Studio 凍結。

-   修正從 Unity 擷取組件的方式，以避免鎖定檔案並造成 Unity 建置流程混淆。

## <a name="1090"></a>1.0.9.0
 發行日期：2012 年 10 月 3 日

### <a name="bug-fixes"></a>Bug 修正

-   修正 Unity 專案包含實際 JavaScript 資產時的專案產生。

-   修正運算式評估中的錯誤處理。

-   修正將新值設定為實值類型欄位的作業。

-   修正滑鼠停留在程式碼編輯器中的運算式上方時可能會有的副作用。

-   修正針對運算式評估在載入組件中搜尋類型的方式。

-   已修正 Bug UVS-21：指派 Unity 物件的評估沒有任何作用。

-   已修正 Bug UVS-21：評估 Unity Math API 的方法引動過程時，指標無效。

## <a name="1080"></a>1.0.8.0
 發行日期：2012 年 9 月 26 日

### <a name="bug-fixes"></a>Bug 修正

-   修正指令碼開啟工具取得專案路徑的方式，以確保能夠同時開啟 Visual Studio 和指令碼。

-   修正偵錯工作階段執行時所建立的中斷點可能會導致 Visual Studio 鎖定的 Bug。

-   修正在 Visual Studio 2010 上註冊 UnityVS 的方式。

## <a name="1070"></a>1.0.7.0
 發行日期：2012 年 9 月 14 日

### <a name="new-features"></a>新功能

-   Visual Studio 2012 支援。

### <a name="bug-fixes"></a>Bug 修正

-   修正 Editor 和 Plugins 專案檔的產生，以符合 Unity 的行為。

-   修正在 Unity 4 上的 .pdb 符號轉譯。

> [!IMPORTANT]
>  由於支援 Visual Studio 2012，我們必須重新命名一些檔案及移動其他一些檔案。 匯入 Unity 的 UnityVS 套件現在命名為 UnityVS 2010 或 UnityVS 2012，分別代表 Visual Studio 2010 和 Visual Studio 2012。 這個版本也需要重新產生 UnityVS 專案檔。

## <a name="1060---internal-build"></a>1.0.6.0 - 內部組建
 發行日期：2012 年 9 月 12 日

## <a name="1050"></a>1.0.5.0
 發行日期：2012 年 9 月 10 日

### <a name="bug-fixes"></a>Bug 修正

-   修正指令碼或著色器有無效的 xml 字元時的專案檔產生。

-   修正 Unity 連接到 Asset 伺服器時的 Unity 執行個體偵測。 這會觸發失敗，以從 Unity 開啟檔案，並自動連接到 Visual Studio 偵錯工具。

## <a name="1040"></a>1.0.4.0
 發行日期：2012 年 9 月 5 日

### <a name="new-features"></a>新功能

-   自動轉換 Unity 中的偵錯符號。

     如果您的 Asset 資料夾中有 .NET .dll 組件及其關聯的 .pdb，只要重新匯入組件，UnityVS 便會將 .pdb 轉換成 Unity 指令碼引擎了解的偵錯符號檔，並且您能夠從 UnityVS 逐步執行 .NET 組件。

### <a name="bug-fixes"></a>Bug 修正

-   修正 Unity 內的方法或屬性擲回之例外狀況造成偵錯時所發生的 UnityVS 損毀。

## <a name="1030"></a>1.0.3.0
 發行日期：2012 年 9 月 4 日

### <a name="new-features"></a>新功能

-   新增組態選項，以停用 UnityVS 從 Unity 開啟檔案的用法。

### <a name="bug-fixes"></a>Bug 修正

-   修正非編輯器專案之 UnityEditor 參考的產生。

-   修正非編輯器專案之 UNITY_EDITOR 符號的定義。

-   修正我們的自訂狀態列所造成的隨機 VS 損毀。

## <a name="1020"></a>1.0.2.0
 發行日期：2012 年 8 月 30 日

### <a name="bug-fixes"></a>Bug 修正

-   修正與 PythonTools 偵錯工具的衝突。

-   修正 Mono.Cecil 的參考。

-   修正從 Unity (使用 Unity 4 b7) 擷取指令碼組件之方式的 Bug。

## <a name="1010"></a>1.0.1.0
 發行日期：2012 年 8 月 28 日

### <a name="new-features"></a>新功能

-   Unity 4.0 Beta 的預覽支援。

### <a name="bug-fixes"></a>Bug 修正

-   修正檢查擲回例外狀況之屬性的作業。

-   修正檢查物件時遞減為基底物件的作業。

-   修正 MonoBehavior 精靈中的 [Insertion point] 下拉式清單空白的問題。

-   修正 UnityScript 和 Boo 的 [Asset] 資料夾內的 DLL 完成。

## <a name="1000---initial-release"></a>1.0.0.0 - 初始版本
 發行日期：2012 年 8 月 22 日
