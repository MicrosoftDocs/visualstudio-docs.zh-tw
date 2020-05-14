---
title: 只是我的代碼 |微軟文檔
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302494"
---
# <a name="just-my-code"></a>Just My Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 .NET Framework 語言的開發人員皆熟悉 Just My Code 偵錯工具功能，此功能於系統、架構以及其他非使用者呼叫逐步執行，並在 [呼叫堆疊] 視窗中摺疊這些呼叫。 Just My Code 已延伸到 JavaScript 和 C++ 語言。 本主題描述在 .NET Framework 專案、原生 C++ 專案以及 JavaScript 專案中使用 Just My Code 的細節。  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> 啟用或停用 Just My Code  
 要啟用或禁用"僅我的代碼"，請選擇 **"調試**"功能表上**的選項和設置**。 在**調試** / **常規**節點中，選擇或清除**僅啟用我的代碼**。  
  
 ![[選項] 對話方塊中的 [啟用 Just My Code]](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> "**僅啟用我的代碼"** 設置是一個全域設置，應用於所有語言的所有 Visual Studio 專案。  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>覆蓋呼叫堆疊篩選  
 在呼叫堆疊的顯示中，例如在 [呼叫堆疊] 和 [工作] 視窗中，Just My Code 會將非使用者程式碼摺疊至標記為 `[External Code]` 標註的框架中。 要查看折疊幀，請選擇呼叫堆疊顯示的內容功能表上顯示**外部代碼**。  
  
> [!NOTE]
> "**顯示外部代碼"** 設置將保存到當前使用者的探測器中。 它會套用至使用者所開啟的所有語言之專案。  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET 框架只是我的代碼  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>使用者和非使用者代碼  
 為了區分使用者代碼和非使用者代碼，僅我的代碼將查看符號 （.pdb） 檔和程式優化。 在最佳化此二進位檔時，或當 .pdb 檔無法使用時，偵錯工具會將程式碼視為非使用者程式碼。  
  
 還有三個屬性也會影響偵錯工具如何判斷 My Code：  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> 會告知偵錯工具它所套用的程式碼並不是 My Code。  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> 會對偵錯工具隱藏程式碼，即使 Just My Code 已關閉。  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> 會告知偵錯工具應逐步執行 (Step Through) 它所套用的程式碼，而非逐步執行 (Step Into) 程式碼。  
  
  其他程式碼可視為使用者程式碼。  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>步進行為  
 當您**進入**（鍵盤快速鍵：F11）非使用者代碼時，調試器將代碼執行到下一個使用者語句。 **當您退出**（鍵盤：移位 + F11）時，調試器將運行到下一行使用者代碼。 如果沒有發現使用者程式碼，則在應用程式結束、叫用中斷點或發生例外狀況之前，都會繼續執行。  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>中斷點行為  
 啟用"僅我的代碼"後，您可以選擇 **"全部中斷**"（鍵盤：Ctrl + Alt = 中斷），並在沒有要顯示的使用者代碼的位置停止執行。 發生這種情況時，就會顯示 [沒有來源] 視窗。 如果您接著選取 [逐步執行] 命令，偵錯工具會將您帶到下一行使用者程式碼。  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>異常行為  
 如果未處理的例外狀況發生在非使用者程式碼，偵錯工具就會在產生例外狀況的該行使用者程式碼中斷。  
  
 假如第一個可能發生的例外狀況已未此例外狀況所啟用，就會以綠色反白顯示使用者程式碼行。 呼叫堆疊顯示標記為 **[外部代碼]** 的帶標籤的幀。  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> C++ Just My Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>使用者和非使用者代碼  
 因為逐步執行行為獨立於呼叫堆疊行為，所以 C++ Just My Code 不同於 .NET Framework 和 JavaScript Just My Code。  
  
 **呼叫堆疊**  
  
 根據預設，此偵錯工具在呼叫堆疊視窗會將這些函式視為非使用者程式碼：  
  
- 在其符號檔中已移除來源資訊之函式。  
  
- 符號檔表示沒有與堆疊框架對應的原始程式檔之函式。  
  
- 在 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 資料夾 `*.natjmc` 檔案中所指定的函式。  
  
  **逐步執行**  
  
  根據預設，只有在 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 資料夾的 `*.natstepfilter` 檔案中指定的函式可視為非使用者程式碼。  
  
  您可以建立自己的 `.natstepfilter` 和 `.natjmc` 來自訂 `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` 中的 [逐步執行] 和 [呼叫堆疊] 視窗行為。  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>步進行為  
 當您從使用者代碼**進入**（鍵盤快速鍵：F11）非使用者代碼時，調試器將執行代碼到下一行使用者代碼。 **當您退出**（鍵盤：移位 + F11）時，調試器將運行到下一行使用者代碼。 如果沒有發現使用者程式碼，則在應用程式結束、叫用中斷點或發生例外狀況之前，都會繼續執行。  
  
 如果偵錯工具在非使用者程式碼內中斷 (例如，如果有個 [全部中斷] 命令於非使用者程式碼停止)，則在非使用者程式碼繼續逐步執行。  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>異常行為  
 當偵錯工具遇到例外狀況時，無論是在使用者或是在非使用者程式碼內，一遇到例外狀況偵錯工具就會停止。 忽略 **"例外"** 對話方塊中的 **"使用者未處理**"選項。  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>自訂步進行為  
 您可以指定函式不進入某程式區段逐步執行 (Step Over)，方法是將其列出，做為 `*.natstepfilter` 檔案中的非使用者程式碼。  
  
- 要為 Visual Studio 電腦的所有使用者指定非使用者代碼，請將 .natstepfilter 檔`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`添加到資料夾中。  
  
- 要為單個使用者指定非使用者代碼，請將 .natstep 篩選器檔添加到`%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`資料夾中。  
  
  .natstep 篩選器檔是具有此語法的 xml 檔：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|元素|描述|  
|-------------|-----------------|  
|函式|必要。 指定一個或多個函式做為非使用者函式。|  
|`Name`|必要。 指定要比對的完整函式名稱之 ECMA-262 格式化規則運算式。 例如：<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> 告知偵錯工具在 `MyNS::MyClass` 中的所有方法要視為非使用者程式碼。 該比對會區分大小寫。|  
|`Module`|選擇性。 指定包含此函式的模組之完整路徑的 ECMA-262 格式化規則運算式。 該比對不區分大小寫。|  
|`Action`|必要。 區分大小寫值的其中之一：<br /><br /> -   `NoStepInto`• 告訴調試器踩過匹配的函數。<br />-   `StepInto`• 告訴調試器進入匹配的函數，重寫匹配函數的任何其他`NoStepInto`函數。|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>自訂呼叫堆疊行為  
 您可以在 `*.natjmc` 檔案指定模組、原始程式檔和函式，將它們指定為在呼叫堆疊中視為非使用者程式碼。  
  
- 要為 Visual Studio 電腦的所有使用者指定非使用者代碼，請將 .natjmc 檔`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`添加到資料夾中。  
  
- 要為單個使用者指定非使用者代碼，請將 .natjmc 檔添加到`%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`資料夾中。  
  
  .natjmc 檔是具有此語法的 xml 檔：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **模組項目屬性**  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 該模組的完整路徑。 您可以使用 Windows 萬用字元 `?` (零或一個字元) 和 `*` (零或多個字元)。 例如，<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> 告知偵錯工具將所有磁碟機上 `\3rdParty\UtilLibs` 中的所有模組視為外部程式碼。|  
|`Company`|選擇性。 發行內嵌於可執行檔之模組的公司名稱。 您可以使用這個屬性使模組意義清楚。|  
  
 **檔案項目屬性**  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 要視為外部程式碼的原始程式檔之完整路徑。 在指定路徑時，您可以使用 Windows 萬用字元 `?` 和 `*`。|  
  
 **Function 項目屬性**  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 要視為外部程式碼的函式之完整名稱。|  
|`Module`|選擇性。 包含此函式的模組名稱或完整路徑。 您可以使用這個屬性使具有相同名稱的函式意義清楚。|  
|`ExceptionImplementation`|當設定為 `true` 時，此呼叫堆疊會顯示擲回例外狀況的函式，而不是這個函式。|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript Just My Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>使用者和非使用者代碼  
 **程式碼分類**  
  
 JavaScript Just My Code 將程式碼分類為下列類別其中一類，來控制逐步執行和呼叫堆疊顯示：  
  
|||  
|-|-|  
|**MyCode**|您所擁有並控制的使用者程式碼。|  
|**LibraryCode**|來自您正常使用且應用程式為正確運作所依賴的程式庫之非使用者程式碼 (例如 WinJS 或 jQuery)。|  
|**UnrelatedCode**|可能在應用程式中運行的非使用者代碼，但您不擁有，並且應用程式不會直接依賴它正常運行（例如，顯示廣告的廣告 SDK）。 在 Windows 市集專案中，也會將從 HTTP 或 HTTPS URI 載入至您應用程式的所有程式碼視為 UnrelatedCode。|  
  
 JavaScript 偵錯工具會自動將這些程式碼類型分類：  
  
- 通過將字串傳遞到主機提供的`eval`函數執行的腳本被歸類為**MyCode**。  
  
- 通過將字串傳遞給建構函式執行的`Function`腳本被歸類為**庫代碼**。  
  
- 包含在框架引用中的腳本（如 WinJS 或 Azure SDK）被歸類為**庫代碼**。  
  
- 通過將字串傳遞到`setTimeout`，`setImmediate`或`setInterval`函數執行的腳本被歸類為**不相關的代碼**。  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` 為所有 Visual Studio JavaScript 專案指定其他使用者和非使用者程式碼。  
  
  您可以修改預設分類，並將名為 `mycode.json` 的 .json 檔案加入專案根資料夾，來分類特定檔案和 URL。  
  
  所有其他程式碼會分類為 **MyCode**。  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>步進行為  
  
- 如果函數不是使用者 （**MyCode**） 代碼，**則"進入**"（鍵盤快速鍵：F11）的行為為 **"單一步驟**"（鍵盤：F10）。  
  
- 如果步驟從非使用者 （**庫代碼**或不**相關的代碼**） 代碼中開始，則步進會暫時執行，就像未啟用"僅我的代碼"一樣。 一旦您倒退回使用者程式碼，Just My Code 逐步執行隨即重新啟用。  
  
- 當使用者程式碼中的步驟造成離開目前執行內容 (例如在事件處理常式的最後一行執行步驟)，偵錯工具將於下一個已執行的使用者程式碼行停止。 例如，如果在**庫庫代碼**中執行回檔，調試器將繼續，直到執行下一行使用者代碼。  
  
- **步出**（鍵盤：移位 + F11）停止在下一行使用者代碼上。 如果沒有發現使用者程式碼，則在應用程式結束、叫用中斷點或發生例外狀況之前，都會繼續執行。  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>中斷點行為  
  
- 不論該程式碼的分類為何，永遠叫用已設定在任何程式碼的中斷點。  
  
- 如果 `debugger` 關鍵字出現在：  
  
  - **庫代碼**，調試器總是中斷。  

  - **不相關的代碼**，調試器不會停止。  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>異常行為  
 假如未處理的例外狀況發生在：  
  
- **MyCode**或**庫代碼**，調試器總是中斷。  
  
- **不相關的代碼**，以及**MyCode**或**庫代碼**位於呼叫堆疊上，調試器中斷。  
  
  如果"例外"對話方塊上的異常啟用了第一次機會異常，並且該異常在**庫庫代碼**或不**相關的代碼**中引發：  
  
- 如果已經處理此例外狀況，則偵錯工具不會中斷。  
  
- 如果例外狀況未經處理，則偵錯工具會中斷。  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>僅自訂我的代碼  
 若要為單一 Visual Studio 專案分類使用者程式碼和非使用者程式碼，請將名為 `mycode.json` 的 .json 檔案加入此專案的根資料夾。  
  
 會依這個順序執行分類：  
  
1. 預設分類  
  
2. 在 `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` 檔案的分類  
  
3. 在目前專案的 `mycode. json` 檔案之分類。  
  
   每個分類步驟都會覆寫先前的步驟。 .json 檔不需要列出所有鍵值對 **，MyCode、****庫**和**不相關的**值可以是空陣列。  
  
   My Code .json 檔案中使用這種語法：  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval、Function 和 ScriptBlock**  
  
 **Eval、****函數**和**腳本塊**鍵值對確定動態生成的代碼的分類方式。  
  
|||  
|-|-|  
|**Eval**|藉由傳遞字串給主機所提供的 `eval` 函式來執行的指令碼。 根據預設，Eval 指令碼會分類為 **MyCode**。|  
|**函數**|藉由傳遞字串給 `Function` 建構函式來執行的指令碼。 根據預設，Function 指令碼會分類為 **LibraryCode**。|  
|**腳本塊**|由傳遞字串給 `setTimeout`、`setImmediate` 或 `setInterval` 函式所執行的指令碼。 根據預設，ScriptBlock 指令碼會分類為 **UnrelatedCode**。|  
  
 您可以變更此值為這些關鍵字之一：  
  
- `MyCode`將腳本分類為**MyCode**。  
  
- `Library`將腳本分類為**庫代碼**。  
  
- `Unrelated`將腳本分類為**不相關代碼**。  
  
  **MyCode、Libraries 和 Unrelated**  
  
  **MyCode、****庫**和**不相關的**鍵值對指定要包含在分類中的 URL 或檔：  
  
|||  
|-|-|  
|**MyCode**|分類為**MyCode**的 URL 或檔陣列。|  
|**程式庫**|分類為**庫代碼**的 URL 或檔陣列。|  
|**Unrelated**|分類為**不相關代碼的**URL 或檔陣列。|  
  
 這個 URL 或檔案字串可以包含一或多個 `*` 字元，這會比對零或多個字元。 `*` 相當於 `.*` 規則運算式。
