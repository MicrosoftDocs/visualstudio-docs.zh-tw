---
title: 變更記錄檔 (Visual Studio Tools for Unity，Mac) | Microsoft Docs
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e817318f7b16040ed598ac4dce8f1c6017bdf83e
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471528"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>變更記錄檔 (Visual Studio Tools for Unity，Mac)

Visual Studio Tools for Unity 變更記錄。

## <a name="2710"></a>2.7.1.0
2020年8月5日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已將 Unity 訊息 API 更新為2019.4。

  - 已新增 [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) 的抑制器 `CA1823` 。 具有或屬性的私用欄位 `SerializeField` `SerializeReference` 不應標記為未使用（FxCop）。
  
  - 已新增 [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) 的抑制器 `CA1822` 。 Unity 訊息不應標示為 `static` 修飾詞（FxCop）的候選項目。

  - 已新增 [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) 的抑制器 `CA1801` 。 不應該從 Unity 訊息（FxCop）移除未使用的參數。
  
  - 已將 `MenuItem` 支援新增至 [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) 抑制器。  

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - Fixed [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) 和 [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) suppressors 無法使用額外的括弧或方法引數。
  
  - 已修正強制資產資料庫重新整理，即使已停用 Unity 設定中的自動重新整理也一樣。

## <a name="2700"></a>2.7.0.0
2020年6月23日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增在 Unity 重新產生方案和專案時保存解決方案資料夾的支援。

  - 已新增 [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) 診斷。 使用或屬性偵測不正確的方法簽章 `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` 。

  - 已新增 [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) 診斷。 搭配 `Invoke` 使用 `InvokeRepeating` 、 `StartCoroutine` 或 `StopCoroutine` 與第一個引數為字串常值，並不是型別安全。

  - 已新增 [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) 診斷。 `SetPixels`調用速度很慢。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正當遊戲在舊版 Mono 執行時間上執行時（嘗試在建立中斷點時立即系結），建立中斷點。 
  
- **整合**

  - 在 Unity message wizard 中篩選訊息時，請勿重設選取範圍。
  
  - 已修正 [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) ， [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 並 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) 使用下列規則 suppressors： `IDE0044` `IDE0051` 針對以 SerializeField 屬性裝飾的所有欄位隱藏（readonly）、（未使用）、 `CS0649` （永不指派）。 `CS0649`針對擴充的所有類型的公用欄位隱藏（永不指派） `Unity.Object` 。

  - 已修正的泛型型別參數檢查 [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) 。

- **求**

  - 已修正與列舉的相等比較。

## <a name="2610"></a>2.6.1.0
2020年5月19日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 如果我們無法在 Unity 端建立訊息伺服器，就會發出警告。

  - 在輕量編譯期間適當地執行分析器。

  - 已修正 Unity Hub 安裝的 API 檔。
  
  - 修正偵錯工具視覺化檢視當機。

## <a name="2600"></a>2.6.0.0
2020年4月14日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) 診斷。 在中偵測並包裝對協同程式的呼叫 `StartCoroutine()` 。

  - 已新增 [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) 診斷。 偵測和移除無效或重複的 `SerializeField` 屬性。

  - 已新增 [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) 診斷。 `GetComponent()`使用非元件或非介面類別型呼叫的偵測。

  - 已新增 [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) 的抑制器 `IDE0051` 。 請不要使用屬性來旗標方法， `ContextMenu` 或使用屬性（attribute）來加以參考（ `ContextMenuItem` 未使用）。

  - 已新增 [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) 的抑制器 `IDE0051` 。 不要將 `ContextMenuItem` 屬性標示為未使用的欄位。

  - 已新增 [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) 的抑制器 `IDE0044` 。 不要讓屬性成為唯讀的欄位 `ContextMenuItem` 。

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)、 [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 和 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) 現在同時適用于 `SerializeReference` 和 `SerializeField` 屬性。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 只有在編輯器能夠進行通訊時，才將開始/停止命令傳送至 Unity。

  - 已修正具有繼承訊息的 QuickInfo 檔。

  - 訊息的固定訊息範圍 `CreateInspectorGUI` 。

  - 不要報告具有多型修飾詞的 [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) 方法。

- **求**

  - 已修正別名 using 的處理。
  
  - 已修正 null 值的處理。  

## <a name="2520"></a>2.5.2.0

2020年3月23日發行

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正附加時的執行緒註冊。

## <a name="2510"></a>2.5.1.0

2020年3月3日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) 的抑制器 `IDE0051` 。 搭配 Invoke、InvokeRepeating、StartCoroutine 或 StopCoroutine 使用的私用方法不應標記為未使用。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正 OnDrawGizmos/OnDrawGizmosSelected 檔。

- **求**

  - 已修正 lambda 引數檢查。

## <a name="2501"></a>2.5.0.1

2020年2月19日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正 [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) 不正確訊息簽章的診斷檢查。 檢查具有多個繼承層級的類型時，此診斷可能會失敗，並出現下列訊息： `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` 。

## <a name="2500"></a>2.5.0.0 起

2020年1月22日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 HLSL 檔案的支援。
  
  - 切換至新的資料夾對話方塊 UI。
  
  - 切換至新的可存取屬性方格以進行設定。

  - 已新增 [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 的抑制器 `IDE0051` 。 具有屬性的私用欄位 `SerializeField` 不應標示為未使用。

  - 已新增 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) 的抑制器 `CS0649` 。 具有屬性的欄位 `SerializeField` 不應標記為未指派。  

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正專案產生（ `GenerateTargetFrameworkMonikerAttribute` 目標不一定是正確的位置）。

- **求**

  - 已修正字串評估（不使用 ToString （）呼叫）

## <a name="2420"></a>2.4.2.0

2019年12月3日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正使用者定義介面的診斷。

  - 已修正具有格式錯誤之運算式的快速工具提示。
  
## <a name="2410"></a>2.4.1.0

2019年11月6日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 Unity 背景進程的支援。 （偵錯工具可以自動連接到主要進程，而不是子進程）。

  - 加入 Unity 訊息的快速工具提示，顯示相關聯的檔。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正 `UNT0002` 具有「先進的二進位」和「調用」運算式的標記比較分析器。

### <a name="deprecated-features"></a>已被取代的功能

- **整合**

  - 接下來，Visual Studio Tools for Unity 只會支援 Visual Studio 2017 +。

## <a name="2400"></a>2.4.0.0

2019年10月15日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已為 [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) `IDE0060` 所有 Unity 訊息新增（未使用的參數）的抑制器。

  - 已為標記為的欄位新增快速工具提示 `TooltipAttribute` 。 （這也適用于使用此欄位的簡單 get 存取子）。

## <a name="2330"></a>2.3.3.0

2019年9月23日發行

### <a name="new-features"></a>新功能

- **整合**

  - 新增 IDE0060 的抑制器，以防止 IDE 顯示快速修正以移除未使用的參數。
    - `USP0005`針對 `IDE0060` ： unity 訊息是由 unity 執行時間叫用。

## <a name="2320"></a>2.3.2.0

2019年9月16日發行

### <a name="new-features"></a>新功能

- **整合**

  - 我們已藉由加入 Unity 專屬的新診斷，來深度對 Unity 專案的瞭解 Visual Studio。 我們也隱藏了對 Unity 專案不適用的通用 C# 診斷，讓 IDE 更有智慧。 例如，IDE 不會顯示快速修正來將偵測器變數變更為， `readonly` 這會讓您無法修改 Unity 編輯器中的變數。
    - `UNT0001`：執行時間會呼叫 Unity 訊息，即使它們是空的，也不會宣告它們來避免 Unity 執行時間處理 uncesseray。
    - `UNT0002`：使用字串相等的標記比較會比內建的 CompareTag 方法慢。
    - `UNT0003`：使用泛型形式的 GetComponent 是型別安全的慣用方法。
    - `UNT0004`：更新訊息會相依于畫面播放速率，而且應該使用 deltaTime 而不是 fixedDeltaTime。
    - `UNT0005`： FixedUpdate 訊息與框架速率無關，應使用 fixedDeltaTime 而不是 deltaTime。
    - `UNT0006`：偵測到此 Unity 訊息的方法簽章不正確。
    - `UNT0007`： Unity 會針對與 null 聯合不相容的 Unity 物件，覆寫 null 比較運算子。
    - `UNT0008`： Unity 會針對與 null 傳播不相容的 Unity 物件，覆寫 null 比較運算子。
    - `UNT0009`：將 InitializeOnLoad 屬性套用至類別時，您必須提供靜態的函式。 InitializeOnLoad 屬性可確保其在編輯器啟動時受到呼叫。
    - `UNT0010`： MonoBehaviours 只能使用 AddComponent （）來建立。 MonoBehaviours 是元素，且應附加至 GameObject。
    - `UNT0011`： ScriptableObject 只能使用 CreateInstance （）來建立。 ScriptableObject 須由 Unity 引擎建立來處理 Unity 訊息方法。
    - `USP0001`針對 `IDE0029` ： Unity 物件不應該使用 null 聯合。
    - `USP0002`針對 `IDE0031` ： Unity 物件不應該使用 null 傳播。
    - `USP0003`針對 `IDE0051` ： unity 訊息是由 unity 執行時間叫用。
    - `USP0004`針對 `IDE0044` ：具有 SerializeField 屬性的欄位不應設為 readonly。

## <a name="2310"></a>2.3.1.0

2019年9月4日發行

### <a name="new-features"></a>新功能

- **求**

  - 已新增對較佳類型顯示的支援，亦即， `List<object>` 而不是 `List'1[[System.Object, <corlib...>]]` 。

  - 已新增對指標成員存取的支援，亦即 `p->data->member` 。

  - 已在陣列初始化運算式中新增隱含轉換的支援，亦即 `new byte [] {1,2,3,4}` 。

  - 已新增在檢查位元組陣列和字串時的十六進位編輯器支援。

## <a name="2300"></a>2.3.0.0

2019年8月13日發行

### <a name="bug-fixes"></a>錯誤修正

- **求**

  - 修正例外狀況的逐步執行問題。

  - 已修正虛擬識別碼的評估（例如 $exception）。

  - 解除引用無效位址時，避免損毀。  

  - 已修正卸載 appdomain 的問題。

## <a name="2200"></a>2.2.0.0

2019 年 7 月 25 日發行

### <a name="bug-fixes"></a>錯誤修正

- **求**

  - 已修正 IntPtr 型別的檢閱。

- **偵錯工具**

  - 已修正捕捉點與函數中斷點的處理方式。

## <a name="2130"></a>2.1.3.0

2019 年 7 月 9 日發行

### <a name="new-features"></a>新功能

- **偵錯工具**

  - 已新增對捕捉例外狀況子類別的支援。

  - 已新增對 MDS 通訊協定 2.5.1 的支援。

- **整合**

  - 已新增對 asmdef 檔案的資源。

  - 從範本新增檔案時切換至重新命名模式 (以模擬 Unity 編輯器行為)。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正與 Unity 播放機通訊時，對格式不正確訊息的處理方式。

- **求**

  - 已修正運算式中命名空間的處理方式。

## <a name="2120"></a>2.1.2.0

2019 年 7 月 2 日發行

### <a name="bug-fixes"></a>錯誤修正

- **求**

  - 已修正包含非可剖析式運算式的錯誤報告。

## <a name="2110"></a>2.1.1.0

2019 年 6 月 27 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已將 MonoBehaviour API 更新為 2019.1。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正 Unity 專案總管效能。

  - 已修正啟用輕量型組建時輸出的報告警告和錯誤。

  - 已修正輕量型組建效能。

## <a name="2100"></a>2.1.0.0

2019 年 6 月 20 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已停用 Unity 專案的完整組建，改為使用 IntelliSense 錯誤和警告。 事實上，Unity 會使用代表 Unity 內部工作的類別庫專案，建立一個 Visual Studio 方案。 也就是說，當 Unity 的編譯管線遭到關閉時，它永遠不會使用或挑選 Visual Studio 中的組建結果。 在 Visual Studio 中建置只是消耗資源而已。 如果您因為有相依的工具或設定而需要完整建置，您可以停用此最佳化 (設定/Tools for Unity/停用專案的完整建置)。
  
  - 已新增對 UPE 中 Unity 封裝的支援。 只有參考套件 (使用 `Packages` 資料夾中的 manifest.json) 和本機套件 (內嵌在 `Packages` 資料夾中) 會顯示。

## <a name="2021"></a>2.0.2.1

2019 年 5 月 30 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 Unity 執行目標的自訂圖示。

## <a name="2020"></a>2.0.2.0

發行於 2019 年 4 月 2 日

### <a name="new-features"></a>新功能

- **整合**

  - 已新增在儲存時自動重新整理 Unity 資產資料庫的支援。 這預設會啟用，且在 Visual Studio 中儲存指令碼時，會觸發在 Unity 端的重新編譯。 您可以在 [工具]\\[選項]\\[Tools for Unity]\\[儲存時重新整理 Unity 的 AssetDatabase] 中停用此功能。

  - 新增針對離線文件設定慣用之 Unity 安裝的支援。

  - 新增新編輯器的快顯功能表。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正組件篩選和空白框架的框架檢查。

## <a name="2011"></a>2.0.1.1
 
 發行於 2019 年 3 月 26 日

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 暫時將 Mono 設定為此版本之預設且唯一可用的偵錯工具。

## <a name="2006"></a>2.0.0.6

發行於 2019 年 3 月 26 日

### <a name="new-features"></a>新功能

- **整合**

  - 新增 [附加至 Unity 並試玩] 的支援。

## <a name="2005"></a>2.0.0.5

發行於 2019 年 3 月 20 日

### <a name="new-features"></a>新功能

- **專案產生：**

  - 處理解決方案檔案時，保留外部屬性。
  
- **求**

  - 已新增對別名限定名稱 (目前僅限於全域命名空間) 的支援。 因此，運算式評估工具現在會接受使用表單 global::namespace.type 的類型。

  - 已新增對 `pointer[index]` 表單的支援，即語意上與指標取值 `*(pointer+index)` 表單相同。

## <a name="2004"></a>2.0.0.4

發行於 2019 年 3 月 5 日

### <a name="new-features"></a>新功能

- **整合**

  - 已更新 `ScriptableObject` API。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 從範本移除命名空間。

## <a name="2003"></a>2.0.0.3
 
 發行於 2019 年 3 月 5 日

### <a name="new-features"></a>新功能

- **專案產生：**

  - 公用和序列化欄位將不會再造成警告。 `CS0649` `IDE0051` 在建立這些訊息的 Unity 專案中，我們已自動隱藏和編譯器警告。

- **整合**

  - 如果有超過一個的 Unity 處理序在執行，系統會提示附加到特定執行個體。

- **求**

  - 新增區域函式的支援。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正使用舊版通訊協定版本時具名變數上的自訂屬性。

## <a name="2002"></a>2.0.0.2

2019 年 2 月 4 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 更新 MonoBehaviour API。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正偵錯工具中的設定基本值。

## <a name="2001"></a>2.0.0.1

發行於 2018 年 12 月 4 日

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正安裝套件自我內含項目。

## <a name="2000"></a>2.0.0.0
 發行於 2018 年 12 月 4 日

### <a name="new-features"></a>新功能

- **偵錯工具**

  - 用 Windows 的相同核心 Unity 偵錯工具，取代 Mac 上的 Unity 偵錯工具。

  - 取代 NRefactory 以利將 Roslyn 用於運算式評估。

  - 已新增指標的支援：取值、轉換和指標計算 (此功能需要 Unity 2018.2+ 和新執行階段)。

  - 新增陣列指標檢視 (如在 C++ 中) 的支援。 接受指標運算式然後附加逗號和您要查看之數目的元素。

  - 新增非同步建構的支援。

  - 新增虛擬變數 (例外狀況和物件識別碼) 的支援。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正對格式不正確或不受支援之運算式的運算式評估。

## <a name="1700"></a>1.7.0.0

發行時間：2018 年 11 月 13 日

### <a name="new-features"></a>新功能

- **偵錯工具**

  - 在 [附加] 對話方塊中新增更多用戶端資訊 (IP、電腦名稱)。

### <a name="bug-fixes"></a>錯誤修正

- **偵錯工具**

  - 已修正用於與 Unity 偵錯工具引擎通訊之程式庫中的死結，該死結造成 Visual Studio 或 Unity 凍結，特別是在按下 [附加到 Unity] 或重新啟動遊戲時。

- **整合**

  - 修正選取其他預設編輯器時的 Unity 外掛程式啟用問題。

  - 修正 Unity 檔案範本建立問題。

## <a name="1602"></a>1.6.0.2

2018 年 7 月 24 日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 針對 Unity 已修正的 Unity 效能 Bug 復原因應措施。

## <a name="1601"></a>1.6.0.1

2018 年 7 月 10 日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 修正了著色器的程式碼著色支援。

## <a name="1600"></a>1.6.0.0

2018 年 7 月 26 日發行

### <a name="bug-fixes"></a>錯誤修正

- **借助**

  - 修正了 OnApplicationFocus 訊息中的錯字。

- **專案產生：**

  - Unity 效能 Bug 的暫時性因應措施：在產生專案時，會快取 MonoIslands。

  - 在使用新 Unity 執行階段時，不會再將可攜式 pdb 轉換成 mdb。

## <a name="1502"></a>1.5.0.2

2018 年 4 月 18 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 新增了基本著色器程式碼完成功能的支援。

  - 新增了在切換著色器檔案中切換註解的支援。

## <a name="1501"></a>1.5.0.1

2018 年 3 月 28 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增 Unity 專案總管中額外範本的支援。

## <a name="1500"></a>1.5.0.0

2018 年 3 月 21 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增偵測和附加至透過 USB 所連線 Android Player 的支援。

## <a name="1403"></a>1.4.0.3

2018 年 3 月 5 日發行

### <a name="new-features"></a>新功能

- **專案產生：**

  - 已新增 Unity 2018.1 中新專案產生器的支援。

- **整合**

  - 已新增專用設定的選項面板。

## <a name="1402"></a>1.4.0.2

2018 年 1 月 24 日發行

### <a name="bug-fixes"></a>錯誤修正

- **專案產生：**

  - 已修正 Mono 版本偵測。

- **整合**

  - 已修正 2018.1 的時間問題和外掛程式啟用問題。

  - 已修正偵測到新播放器時的通知。

## <a name="1401"></a>1.4.0.1

2018 年 1 月 23 日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正按兩下時展開/摺疊資料夾

## <a name="1400"></a>1.4.0.0

2017 年 12 月 13 日發行

### <a name="new-features"></a>新功能

- **專案產生：**

  - 已新增 .NET Standard 的支援。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 修正自動化 pdb 對 mdb 的偵錯符號轉換。

## <a name="1301"></a>1.3.0.1

2017 年 12 月 12 日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正在嘗試變更陣列大小期間，間接呼叫 EditorPrefs.GetBool 對檢查的影響。

- **借助**

  - 再插入方法之前先重新整理 Roslyn 內容。

## <a name="1300"></a>1.3.0.0

2017 年 11 月 20 日發行

### <a name="new-features"></a>新功能

- **借助**

  - 已新增 [實作 Unity Messages 精靈]。

  - 已新增 VS for Mac 7.4 中新完成 API 的支援。

## <a name="1200"></a>1.2.0.0

2017 年 10 月 23 日發行

### <a name="new-features"></a>新功能

- **偵錯工具**

  - 已新增可攜式偵錯符號檔的支援。

### <a name="bug-fixes"></a>錯誤修正

- **專案產生：**

  - 已修正錯誤新增至組件檔名的額外 .dll 副檔名。

  - 因為預設值現在是 'true'，所以請不要強制執行 AllowAttachedDebuggingOfEditor Unity 旗標。

## <a name="1103"></a>1.1.0.3

2017 年 10 月 23 日發行

### <a name="new-features"></a>新功能

- **專案產生：**

  - 已新增對 .NET 4.6 設定檔的支援。

## <a name="1102"></a>1.1.0.2

2017 年 8 月 8 日發行

### <a name="new-features"></a>新功能

- **偵錯工具**

  - 如果不確定要附加的 Unity，請啟動 [附加到處理序] 對話方塊。

- **專案產生：**

  - 使用 Unity 5.6 時，總是啟用不安全的編譯參數。

## <a name="1101"></a>1.1.0.1

2017 年 7 月 20 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增當地語系化資源的支援。

## <a name="1100"></a>1.1.0.0

2017 年 7 月 12 日發行

### <a name="new-features"></a>新功能

- **整合**

  - 已新增透過 [附加至處理序] 視窗附加至播放器和編輯器的支援。

- **專案產生：**

  - 使用 mcs.rsp 檔案修正組件名稱參考。

  - 已新增 assembly.json 編譯單位的支援。

  - 修正具有 API 層級的定義。

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正編譯時的著色器錯誤訊息。

## <a name="1001"></a>1.0.0.1

2017 年 5 月 4 日發行

### <a name="bug-fixes"></a>錯誤修正

- **整合**

  - 已修正混合式和一般專案的作用中文件追蹤。

## <a name="1000"></a>1.0.0.0

2017 年 5 月 3 日發行
