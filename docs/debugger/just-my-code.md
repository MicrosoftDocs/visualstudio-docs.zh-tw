---
title: 使用者程式碼，Just My code 偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a2873f691fdaa1251a5562e21e2bbd0467eb2e2
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612749"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>指定是否只使用 Just My Code，Visual Studio 中的使用者程式碼偵錯
您可以設定 Visual Studio 自動不進入系統、 架構和其他非使用者呼叫，並摺疊這些呼叫，在 [呼叫堆疊] 視窗中。 啟用或停用此行為的功能稱為*Just My Code*。 本主題描述如何在 C#、 Visual Basic、 c + + 和 JavaScript 專案中使用 Just My Code。

對於大部分的程式設計語言，預設會啟用 Just My Code。
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> 啟用或停用 Just My Code  
 若要啟用或停用 Just My Code，請選擇**工具 > 選項**Visual Studio 中的功能表。 在 **偵錯** > **一般**節點，選擇或清除**啟用 Just My Code**。
  
 ![啟用 Just My Code，在 [選項] 對話方塊](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **啟用 Just My Code**設定是套用至所有語言中的所有 Visual Studio 專案的全域設定。  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> 在 呼叫堆疊檢視中顯示非使用者程式碼  
 在檢視中顯示呼叫堆疊，例如**呼叫堆疊**並**工作**windows，Just My Code 將非使用者程式碼摺疊至標記為註解框架`[External Code]`。 若要檢視摺疊的框架，請選擇**顯示外部程式碼**顯示呼叫堆疊的操作功能表上。

 ![在 [呼叫堆疊] 視窗中顯示外部程式碼](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  **顯示外部程式碼**設定會儲存到目前的使用者程式碼剖析工具。 它會套用至使用者所開啟的所有語言之專案。

##  <a name="identify-user-code-while-debugging"></a>識別使用者程式碼進行偵錯時 

**模組**視窗可以告訴您哪些程式碼模組中偵錯工具會視為使用者程式碼或我的程式碼，以及例如符號載入模組的狀態資訊。 如需詳細資訊，請參閱 <<c0> [ 更熟悉的偵錯工具附加至您的應用程式的方式](../debugger/debugger-tips-and-tricks.md#modules_window)。
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> .NET framework Just My Code  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> 使用者和非使用者程式碼  
 為了區別使用者程式碼從非使用者程式碼，Just My Code 會查看符號 (.pdb) 檔和程式最佳化。 在最佳化此二進位檔時，或當 .pdb 檔無法使用時，偵錯工具會將程式碼視為非使用者程式碼。
  
 還有三個屬性也會影響偵錯工具如何判斷 My Code：  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> 會告知偵錯工具它所套用的程式碼並不是 My Code。  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> 會對偵錯工具隱藏程式碼，即使 Just My Code 已關閉。  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> 會告知偵錯工具應逐步執行 (Step Through) 它所套用的程式碼，而非逐步執行 (Step Into) 程式碼。  
  
 其他程式碼可視為使用者程式碼。  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> 逐步執行行為  
 當您**逐步執行**(鍵盤快速鍵： F11) 非使用者程式碼、 程式碼的偵錯工具步驟下, 一個使用者陳述式。 當您**跳離函式**(鍵盤： Shift + F11)，偵錯工具執行至下一行使用者程式碼。 如果不遇到任何使用者程式碼時，則會繼續執行直到應用程式就會結束，叫用中斷點時，或發生例外狀況。  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> 中斷點行為  
 啟用 Just My Code 時，您可以選擇**全部中斷**(鍵盤： Ctrl + Alt + Break)，並停止執行的位置沒有顯示任何使用者程式碼。 發生這種情況時，就會顯示 [沒有來源] 視窗。 如果您接著選取 [逐步執行] 命令，偵錯工具會將您帶到下一行使用者程式碼。  
  
###  <a name="BKMK_NET_Exception_behavior"></a> 例外狀況行為  
 如果未處理的例外狀況發生在非使用者程式碼，偵錯工具就會在產生例外狀況的該行使用者程式碼中斷。  
  
 假如第一個可能發生的例外狀況已未此例外狀況所啟用，就會以綠色反白顯示使用者程式碼行。 呼叫堆疊會顯示標示為已標註的框架 **[外部程式碼]**。  
  
##  <a name="BKMK_C___Just_My_Code"></a> C + + Just My Code  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> 使用者和非使用者程式碼  
因為逐步執行行為獨立於呼叫堆疊行為，所以 C++ Just My Code 不同於 .NET Framework 和 JavaScript Just My Code。  

從 Visual Studio 2017 15.8 開始，您可以指定是否要為 c + + 使用啟用 Just My Code**工具** > **選項** > **偵錯** > **一般** > **啟用 Just My Code** （它預設啟用）。 這相當於使用[/JMC （只 my code 偵錯）](/cpp/build/reference/jmc)編譯器參數。
  
 **呼叫堆疊**  
  
 根據預設，此偵錯工具在呼叫堆疊視窗會將這些函式視為非使用者程式碼：  
  
-   在其符號檔中已移除來源資訊之函式。  
  
-   符號檔表示沒有與堆疊框架對應的原始程式檔之函式。  
  
-   在 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 資料夾 `*.natjmc` 檔案中所指定的函式。  
  
 **逐步執行**  
  
 根據預設，只有在 `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` 資料夾的 `*.natstepfilter` 檔案中指定的函式可視為非使用者程式碼。  
  
 您可以建立自己的 `.natstepfilter` 和 `.natjmc` 來自訂 `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` 中的 [逐步執行] 和 [呼叫堆疊] 視窗行為。  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> 逐步執行行為  
 當您**逐步執行**(鍵盤快速鍵： F11) 從使用者程式碼的非使用者程式碼、 偵錯工具不進入程式碼至下一行使用者程式碼。 當您**跳離函式**(鍵盤： Shift + F11)，偵錯工具執行至下一行使用者程式碼。 如果不遇到任何使用者程式碼時，則會繼續執行直到應用程式就會結束，叫用中斷點時，或發生例外狀況。  
  
 如果偵錯工具在非使用者程式碼內中斷 (例如，如果有個 [全部中斷] 命令於非使用者程式碼停止)，則在非使用者程式碼繼續逐步執行。
  
###  <a name="BKMK_CPP_Exception_behavior"></a> 例外狀況行為  
 當偵錯工具叫用例外狀況時，它會停止的例外狀況，而不論其是否在使用者或非使用者程式碼。 **User-unhandled**中的選項**例外狀況**對話方塊都會被忽略。  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> 自訂逐步執行行為  
 您可以指定函式不進入某程式區段逐步執行 (Step Over)，方法是將其列出，做為 `*.natstepfilter` 檔案中的非使用者程式碼。  
  
-   若要指定非使用者程式碼，在 Visual Studio 電腦的所有使用者，新增 .natstepfilter 檔案到`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`資料夾。  
  
-   若要指定非使用者程式碼，針對個別使用者，新增 .natstepfilter 檔案到`%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`資料夾。  
  
 .natstepfilter 檔案是 xml 檔案，具有如下語法：  
  
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
|功能|必要。 指定一個或多個函式做為非使用者函式。|  
|`Name`|必要。 指定要比對的完整函式名稱之 ECMA-262 格式化規則運算式。 例如: <br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> 告知偵錯工具在 `MyNS::MyClass` 中的所有方法要視為非使用者程式碼。 該比對會區分大小寫。|  
|`Module`|選擇性。 指定包含此函式的模組之完整路徑的 ECMA-262 格式化規則運算式。 該比對不區分大小寫。|  
|`Action`|必要。 區分大小寫值的其中之一：<br /><br /> -   `NoStepInto`  -會告知偵錯工具不進入符合的函式。<br />-   `StepInto`  -會告知偵錯工具逐步執行比對函式中，覆寫任何其他`NoStepInto`符合的函式。|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> 自訂呼叫堆疊行為  
 您可以在 `*.natjmc` 檔案指定模組、原始程式檔和函式，將它們指定為在呼叫堆疊中視為非使用者程式碼。  
  
-   若要指定非使用者程式碼，在 Visual Studio 電腦的所有使用者，新增 .natjmc 檔案到`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`資料夾。  
  
-   若要指定非使用者程式碼，針對個別使用者，新增 .natjmc 檔案到`%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`資料夾。  
  
 .natjmc 檔案是 xml 檔案，具有如下語法：  
  
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
|`Name`|必要。 該模組的完整路徑。 您可以使用 Windows 萬用字元`?`（零或一個字元） 和`*`（零或多個字元）。 例如，套用至物件的<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 告知偵錯工具將所有磁碟機上 `\3rdParty\UtilLibs` 中的所有模組視為外部程式碼。|  
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
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript Just My Code  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> 使用者和非使用者程式碼  
 **程式碼分類**  
  
 JavaScript Just My Code 將程式碼分類為下列類別其中一類，來控制逐步執行和呼叫堆疊顯示：  
  
|||  
|-|-|  
|**MyCode**|您所擁有並控制的使用者程式碼。|  
|**LibraryCode**|來自您正常使用且應用程式為正確運作所依賴的程式庫之非使用者程式碼 (例如 WinJS 或 jQuery)。|  
|**UnrelatedCode**|無法執行您的應用程式，但是您的非使用者程式碼並不擁有它和您的應用程式並不依賴它才能正確運作。 （例如，這可能包括廣告顯示廣告的 SDK。）在 UWP 專案中，載入至您的應用程式，從 HTTP 或 HTTPS URI 的任何程式碼也會被視為 UnrelatedCode。|  
  
 JavaScript 偵錯工具會自動將這些程式碼類型分類：  
  
-   執行由傳遞字串給主機所提供的指令碼`eval`函式分為**MyCode**。  
  
-   執行由傳遞字串給指令碼`Function`建構函式分為**LibraryCode**。  
  
-   Framework 參考，例如 WinJS 或 Azure SDK 中包含的指令碼分為**LibraryCode**。  
  
-   執行由傳遞字串給指令碼`setTimeout`， `setImmediate`，或`setInterval`函式會分類為**UnrelatedCode**。  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` 為所有 Visual Studio JavaScript 專案指定其他使用者和非使用者程式碼。  
  
 您可以修改預設分類，並將名為 `mycode.json` 的 .json 檔案加入專案根資料夾，來分類特定檔案和 URL。  
  
 所有其他程式碼分為**MyCode**。  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> 逐步執行行為  
  
-   如果函式不是使用者 (**MyCode**) 的程式碼，**逐步**(鍵盤快速鍵： F11) 行為會如同**不進入函式**(鍵盤： F10)。  
  
-   如果在步驟一開始會處於非使用者 (**LibraryCode**或是**UnrelatedCode**) 程式碼，然後逐步執行暫時的行為就如同 Just My Code 未啟用。 當您倒退回使用者程式碼，Just My Code 逐步執行隨即重新啟用。  
  
-   當使用者程式碼中的步驟造成離開目前執行內容 (例如在事件處理常式的最後一行執行步驟)，偵錯工具將於下一個已執行的使用者程式碼行停止。 例如，如果在執行回呼**LibraryCode**偵錯工具會繼續執行，直到下的一行使用者程式碼執行的程式碼。
  
-   **跳離函式**(鍵盤： Shift + F11) 會停止在下一行使用者程式碼。 如果不遇到任何使用者程式碼時，則會繼續執行直到應用程式就會結束，叫用中斷點時，或發生例外狀況。  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> 中斷點行為  
  
-   程式碼中設定的中斷點會一律被叫用不論該程式碼的分類  
  
-   如果 `debugger` 關鍵字出現在：  
  
    -   **LibraryCode**程式碼，偵錯工具一定中斷。  
  
    -   **UnrelatedCode**程式碼，偵錯工具並不會停止。  
  
###  <a name="BKMK_JS_Exception_behavior"></a> 例外狀況行為  
 假如未處理的例外狀況發生在：  
  
-   **MyCode**或是**LibraryCode**程式碼，偵錯工具一定中斷。  
  
-   **UnrelatedCode**程式碼，並**MyCode**或是**LibraryCode**程式碼位於呼叫堆疊偵錯工具中斷。  
  
 如果第一個可能的例外狀況啟用的例外狀況 對話方塊中，且會擲回例外狀況**LibraryCode**或是**UnrelatedCode**程式碼：  
  
-   如果處理的例外狀況，偵錯工具不會中斷。  
  
-   如果例外狀況未經處理，則偵錯工具會中斷。  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> 自訂 Just My Code  
 若要為單一 Visual Studio 專案分類使用者程式碼和非使用者程式碼，請將名為 `mycode.json` 的 .json 檔案加入此專案的根資料夾。  
  
 會依這個順序執行分類：  
  
1.  預設分類  
  
2.  在 `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` 檔案的分類  
  
3.  在目前專案的 `mycode. json` 檔案之分類。  
  
 每個分類步驟都會覆寫先前的步驟。 .Json 檔案不需要列出所有的機碼值組，而**MyCode**，**程式庫**，並**Unrelated**值可以是空的陣列。  
  
 My Code .json 檔案中使用這種語法：  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Eval、 Function 和 ScriptBlock**  
  
 **Eval**，**函式**，並**ScriptBlock**機碼值組決定如何以動態方式產生的程式碼之分類。  
  
|||  
|-|-|  
|**評估版**|藉由傳遞字串給主機所提供的 `eval` 函式來執行的指令碼。 根據預設，Eval 指令碼之分類為**MyCode**。|  
|**Function**|藉由傳遞字串給 `Function` 建構函式來執行的指令碼。 根據預設，函式的指令碼之分類為**LibraryCode**。|  
|**指令碼區塊**|由傳遞字串給 `setTimeout`、`setImmediate` 或 `setInterval` 函式所執行的指令碼。 根據預設，ScriptBlock 指令碼之分類為**UnrelatedCode**。|  
  
 您可以變更此值為這些關鍵字之一：  
  
-   `MyCode`  將做為指令碼分類**MyCode**。  
  
-   `Library`  將做為指令碼分類**LibraryCode**。  
  
-   `Unrelated`  將做為指令碼分類**UnrelatedCode**。  
  
 **MyCode、 Libraries 和不相關**  
  
 **MyCode**，**程式庫**，並**Unrelated**機碼值組指定的 url 或您想要包含在某個分類中的檔案：  
  
|||  
|-|-|  
|**MyCode**|分類為的檔案或 url 的陣列**MyCode**。|  
|**程式庫**|分類為的檔案或 url 的陣列**LibraryCode**。|  
|**不相關的**|分類為的檔案或 url 的陣列**UnrelatedCode**。|  
  
 這個 URL 或檔案字串可以包含一或多個 `*` 字元，這會比對零或多個字元。 `*` 相當於 `.*` 規則運算式。
