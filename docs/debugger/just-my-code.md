---
title: 使用者程式碼，Just My code 偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01e36c528b71bb49b29265890ca6c48863f01be9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389023"
---
# <a name="debug-only-user-code-with-just-my-code"></a>只有使用 Just My Code 的使用者程式碼進行偵錯 

*Just My Code*超出 Visual Studio 偵錯功能自動步驟系統、 架構和其他非使用者程式碼的呼叫。 在 [**呼叫堆疊**] 視窗中，Just My Code 會摺疊這些呼叫 **[外部程式碼]** 框架。 

Just My Code.NET Framework、 c + + 和 JavaScript 專案中的運作方式。

##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> 啟用或停用 Just My Code  

對於大部分的程式設計語言，預設會啟用 Just My Code。 

- 若要啟用或停用 Just My Code，Visual Studio 中，在底下**工具** > **選項**(或**偵錯** > **選項**) >**偵錯** > **一般**中，選取或取消選取**啟用 Just My Code**。
  
 ![啟用 Just My Code，在 [選項] 對話方塊](../debugger/media/dbg_justmycode_options.png "啟用 Just My Code")  
  
> [!NOTE]
> **啟用 Just My Code**是適用於所有語言中的所有 Visual Studio 專案的全域設定。  
  
##  <a name="just-my-code-debugging"></a>Just My Code 偵錯

偵錯工作階段中，**模組**視窗中顯示哪些程式碼偵錯工具視為 My Code （使用者程式碼） 的模組以及其符號載入狀態。 如需詳細資訊，請參閱 <<c0> [ 更熟悉的偵錯工具附加至您的應用程式的方式](../debugger/debugger-tips-and-tricks.md#modules_window)。

 ![在 [模組] 視窗中的使用者程式碼](../debugger/media/dbg_justmycode_module.png "[模組] 視窗中的使用者程式碼")
  
在 [**呼叫堆疊**或是**工作**] 視窗中，Just My Code 將非使用者程式碼摺疊至標記為灰色註解的程式碼框架`[External Code]`。

 ![在 [呼叫堆疊] 視窗中的外部程式碼框架](../debugger/media/dbg_justmycode_externalcode.png "外部程式碼框架")
  
>[!TIP]
>若要開啟 **模組**，**呼叫堆疊**，**工作**，或大部分其他偵錯視窗，您必須在偵錯工作階段。 偵錯時，底下**偵錯** > **Windows**，選取您想要開啟的視窗。 

<a name="BKMK_Override_call_stack_filtering"></a> 若要檢視中摺疊程式碼 **[外部程式碼]** 框架中，以滑鼠右鍵按一下**呼叫堆疊**或是**工作**視窗中，然後選取**顯示外部程式碼**從內容功能表。 展開的外部程式碼行取代 **[外部程式碼**] 框架。 

 ![在 [呼叫堆疊] 視窗中顯示外部程式碼](../debugger/media/dbg_justmycode_showexternalcode.png "顯示外部程式碼")
  
> [!NOTE]
> **顯示外部程式碼**目前的使用者分析工具，設定會套用到使用者所開啟的所有語言中的所有專案。

按兩下在展開的外部程式碼行**呼叫堆疊**視窗會反白顯示呼叫端的程式碼行，以在原始程式碼中的綠色。 Dll 或其他模組找不到或載入，符號或原始程式找不到可能會開啟頁面。

##  <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Just My Code 

在.NET Framework 專案中，Just My Code 會使用符號 (*.pdb*) 檔案和程式最佳化分類使用者和非使用者程式碼。 .NET Framework 偵錯工具會考慮最佳化二進位檔和非粗體 *.pdb*非使用者程式碼的檔案。
  
三個編譯器屬性也會影響.NET 偵錯工具會考慮使用者程式碼：  

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> 告知偵錯工具，它會套用到的程式碼不是使用者程式碼。  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> 會對偵錯工具隱藏程式碼，即使 Just My Code 已關閉。  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> 會告知偵錯工具逐步執行程式碼，它會套用到，而不是逐步執行程式碼。  

.NET Framework 偵錯工具會考慮所有使用者程式碼的程式碼。  

在.NET Framework 偵錯：

- **偵錯** > **逐步**(或**F11**) 上非使用者程式碼不進入程式碼至下一行使用者程式碼。 
- **偵錯** > **跳離函式**(或**Shift**+**F11**) 在非使用者程式碼會執行到下一行使用者程式碼。 

如果沒有更多的使用者程式碼，繼續進行偵錯直到結束、 叫用另一個中斷點，或擲回錯誤。 

<a name="BKMK_NET_Breakpoint_behavior"></a> 如果偵錯工具中斷非使用者程式碼中 (比方說，您會使用**偵錯** > **全部中斷** 和 在非使用者程式碼中的暫停)，則**沒有來源** 視窗隨即出現。 然後您可以使用**偵錯** > **步驟**命令來移至下一行使用者程式碼。

如果非使用者程式碼中發生未處理的例外狀況，偵錯工具會中斷使用者程式碼行，產生的例外狀況。  
  
如果啟用 例外狀況的第一個可能的例外狀況，則呼叫使用者程式碼行是以在原始程式碼中的綠色反白顯示。 **呼叫堆疊** 視窗會顯示標示為標註的框架 **[外部程式碼]**。  

##  <a name="BKMK_C___Just_My_Code"></a> C++ Just My Code  
  
在 c + +，啟用 Just My Code 是使用相同[/JMC （只 my code 偵錯）](/cpp/build/reference/jmc)編譯器參數。

<a name="BKMK_CPP_User_and_non_user_code"></a> Just My Code 會比在.NET Framework 和 JavaScript、 c + + 中的不同，因為您可以指定逐步執行行為，分別為非使用者檔案和**呼叫堆疊**視窗。 

Just My Code，c + + 中會考量這些非使用者程式碼函式：

- 針對**呼叫堆疊**視窗： 

  - 在其符號檔中已移除來源資訊之函式。  
  - 符號檔表示沒有與堆疊框架對應的原始程式檔之函式。  
  - 中指定的函式 *\*.natjmc*中的檔案 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*資料夾。  
  
- 逐步執行行為：
  
  - 中指定的函式 *\*.natstepfilter*中的檔案 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*資料夾。  
  
您可以建立 *.natstepfilter*並 *.natjmc*檔案，以自訂 Just My Code 逐步執行行為並**呼叫堆疊**視窗。 請參閱[自訂 c + + 逐步執行行為](#BKMK_CPP_Customize_stepping_behavior)並[自訂 c + + 呼叫堆疊行為](#BKMK_CPP_Customize_call_stack_behavior)。 

<a name="BKMK_CPP_Stepping_behavior"></a> 在 c + + 偵錯：

- **偵錯** > **逐步**(或**F11**) 上非使用者程式碼不進入程式碼至下一行使用者程式碼。 
- **偵錯** > **跳離函式**(或**Shift**+**F11**) 在非使用者程式碼會執行到下一行使用者程式碼。 

如果沒有更多的使用者程式碼，繼續進行偵錯直到結束、 叫用另一個中斷點，或擲回錯誤。 

如果偵錯工具中斷非使用者程式碼中 (例如，您使用**偵錯** > **全部中斷**和非使用者程式碼中暫停)，在非使用者程式碼繼續逐步執行。

如果偵錯工具叫用例外狀況時，它會停止的例外狀況，無論是在使用者或非使用者程式碼。 **使用者未處理**中的選項**例外狀況設定**對話方塊都會被忽略。  

###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> 自訂 c + + 逐步執行行為  

 在 c + + 專案中，您可以指定函式依其列出中的非使用者程式碼逐步 *\*.natstepfilter*檔案。  
  
- 若要指定非使用者程式碼，為所有本機 Visual Studio 使用者，新增 *.natstepfilter*的檔案 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*資料夾。  
- 若要指定非使用者程式碼，針對個別使用者，新增 *.natstepfilter*的檔案 *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers*資料夾。  
  
A *.natstepfilter*檔案是 XML 檔案使用此語法：  
  
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
|`Function`|必要。 指定一個或多個函式做為非使用者函式。|  
|`Name`|必要。 指定要比對的完整函式名稱之 ECMA-262 格式化規則運算式。 例如: <br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> 告知偵錯工具在 `MyNS::MyClass` 中的所有方法要視為非使用者程式碼。 該比對會區分大小寫。|  
|`Module`|選擇性。 指定包含此函式的模組之完整路徑的 ECMA-262 格式化規則運算式。 該比對不區分大小寫。|  
|`Action`|必要。 區分大小寫值的其中之一：<br /><br /> `NoStepInto`  -會告知偵錯工具不進入函式。<br /> `StepInto`  -會告知偵錯工具逐步執行函式中，覆寫任何其他`NoStepInto`相符的函式。|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> 自訂 c + + 呼叫堆疊行為  

C + + 專案，您可以指定模組、 原始程式檔和函式**呼叫堆疊**藉由指定在視窗會將視為非使用者程式碼 *\*.natjmc*檔案。  
  
-   若要指定非使用者程式碼，在 Visual Studio 電腦的所有使用者，新增 *.natjmc*的檔案 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*資料夾。  
-   若要指定非使用者程式碼，針對個別使用者，新增 *.natjmc*的檔案 *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers*資料夾。  

A *.natjmc*檔案是 XML 檔案使用此語法：  
  
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
|`Name`|必要。 該模組的完整路徑。 您可以使用 Windows 萬用字元`?`（零或一個字元） 和`*`（零或多個字元）。 例如，套用至物件的<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 會告知偵錯工具中的所有模組都視為*\3rdParty\UtilLibs*為外部程式碼的任何磁碟機上。|  
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

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript Just My Code 將程式碼分類為下列類別其中一類，來控制逐步執行和呼叫堆疊顯示：  

|||  
|-|-|  
|**MyCode**|您所擁有並控制的使用者程式碼。|  
|**LibraryCode**|從您經常使用的程式庫和您的應用程式的非使用者程式碼依賴運作正確 （例如 WinJS 或 jQuery）。|  
|**UnrelatedCode**|您不屬於您的應用程式和您的應用程式中的非使用者程式碼不依賴才能正確運作。 例如，廣告顯示廣告的 SDK 可能 UnrelatedCode。 在 UWP 專案中，載入至您的應用程式，從 HTTP 或 HTTPS URI 的任何程式碼也會被視為 UnrelatedCode。|  

JavaScript 偵錯工具會將分類為使用者或依此順序的非使用者程式碼：  
  
1. 預設分類。  
   -   執行由傳遞字串給主機所提供的指令碼`eval`函式**MyCode**。  
   -   執行由傳遞字串給指令碼`Function`建構函式**LibraryCode**。  
   -   Framework 參考，例如 WinJS 或 Azure SDK 中的指令碼**LibraryCode**。  
   -   執行由傳遞字串給指令碼`setTimeout`， `setImmediate`，或`setInterval`函式會**UnrelatedCode**。  
   
2. 針對所有的 Visual Studio JavaScript 專案中指定的分類 *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json*檔案。  
   
3. 中的分類*mycode.json*目前專案的檔案。  
  
每個分類步驟都會覆寫先前的步驟。 

所有其他程式碼會分類為 **MyCode**。  

您可以修改預設分類，並為使用者或非使用者程式碼，分類特定檔案和 Url，加上 *.json*檔案名*mycode.json*到 JavaScript 專案的根資料夾。 請參閱[自訂 JavaScript Just My Code](#BKMK_JS_Customize_Just_My_Code)。 

<a name="BKMK_JS_Stepping_behavior"></a> 在 JavaScript 偵錯： 

- 如果函式為非使用者程式碼中，**偵錯** > **逐步**(或**F11**) 的行為與相同**偵錯** > **不進入函式**(或**F10**)。  
- 如果在步驟一開始會處於非使用者 (**LibraryCode**或是**UnrelatedCode**) 程式碼，逐步執行暫時的行為就如同 Just My Code 未啟用。 當您倒退回使用者程式碼，Just My Code 逐步執行隨即重新啟用。  
- 當使用者程式碼步驟造成離開目前的執行內容時，偵錯工具停止於下一步 執行的使用者程式碼。 例如，如果回呼於 **LibraryCode** 程式碼中執行，則偵錯工具會繼續執行，直到下一行使用者程式碼執行為止。
- **跳離函式**(或**Shift**+**F11**) 會停止在下一行使用者程式碼。 

如果沒有更多的使用者程式碼，繼續進行偵錯直到結束、 叫用另一個中斷點，或擲回錯誤。 

程式碼中設定的中斷點一定會叫用，但程式碼之分類。  

- 如果`debugger`出現在關鍵字**LibraryCode**，偵錯工具一定中斷。  
- 如果`debugger`出現在關鍵字**UnrelatedCode**，並不會停止偵錯工具。  
  
<a name="BKMK_JS_Exception_behavior"></a> 如果在發生未處理的例外狀況**MyCode**或是**LibraryCode**程式碼，偵錯工具一定中斷。  

如果在發生未處理的例外狀況**UnrelatedCode**，和**MyCode**或是**LibraryCode**位於呼叫堆疊偵錯工具中斷。  
  
如果啟用 first-chance 例外狀況的例外狀況，並在發生例外狀況**LibraryCode**或是**UnrelatedCode**:  
  
-   如果已經處理此例外狀況，則偵錯工具不會中斷。  
-   如果例外狀況未經處理，則偵錯工具會中斷。  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> 自訂 JavaScript Just My Code  

分類使用者和非使用者程式碼，為單一的 JavaScript 專案，您可以加入 *.json*檔案名*mycode.json*到專案的根資料夾。  
  
此檔案中的規格覆寫預設分類並*mycode.default.wwa.json*檔案。 *Mycode.json*檔案不需要列出所有的機碼值組。 **MyCode**，**程式庫**，並**Unrelated**值可以是空的陣列。  
  
*Mycode.json*檔案使用此語法：  
  
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
  
 **Eval、Function 和 ScriptBlock**  
  
 **Eval**、**Function** 和 **ScriptBlock** 索引鍵值組會判斷要如何分類動態產生的程式碼：  
  
|||  
|-|-|  
|**Eval**|藉由傳遞字串給主機所提供的 `eval` 函式來執行的指令碼。 根據預設，Eval 指令碼會分類為 **MyCode**。|  
|**Function**|藉由傳遞字串給 `Function` 建構函式來執行的指令碼。 根據預設，Function 指令碼會分類為 **LibraryCode**。|  
|**ScriptBlock**|由傳遞字串給 `setTimeout`、`setImmediate` 或 `setInterval` 函式所執行的指令碼。 根據預設，ScriptBlock 指令碼會分類為 **UnrelatedCode**。|  
  
 您可以變更此值為這些關鍵字之一：  
  
-   `MyCode` 將此指令碼分類為 **MyCode**。  
-   `Library` 將此指令碼分類為 **LibraryCode**。  
-   `Unrelated` 將此指令碼分類為 **UnrelatedCode**。  
  
  **MyCode、Libraries 和 Unrelated**  
  
 **MyCode**、**Libraries** 和 **Unrelated** 索引鍵值組會指定您在分類中要包含的 URL 或檔案：  
  
|||  
|-|-|  
|**MyCode**|分類為 **MyCode** 的 URL 陣列或檔案陣列。|  
|**Libraries**|分類為 **LibraryCode** 的 URL 陣列或檔案陣列。|  
|**Unrelated**|分類為 **UnrelatedCode** 的 URL 陣列或檔案陣列。|  
  
 URL 或檔案字串可以有一或多個`*`比對零或多個字元的字元。 `*` 規則運算式與相同`.*`。
