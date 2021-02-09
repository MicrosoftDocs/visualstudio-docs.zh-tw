---
title: 使用 Just My Code 來調試使用者程式碼 |Microsoft Docs
description: Just My Code 是一項偵錯工具，會自動對非使用者程式碼的呼叫進行步驟。 瞭解如何啟用、停用及使用這項功能。
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d4ea8bb6a1d03d3b61ab5be51992a7b51f661d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893252"
---
# <a name="debug-only-user-code-with-just-my-code"></a>僅使用 Just My Code 的使用者程式碼進行偵錯工具

*Just My Code* 是一種 Visual Studio 的偵錯工具，會自動對系統、架構和其他非使用者程式碼的呼叫進行步驟。 在 [ **呼叫堆疊** ] 視窗中，Just My Code 將這些呼叫折迭至 **[外部程式碼]** 畫面格。

在 .NET、c + + 和 JavaScript 專案中，Just My Code 的運作方式不同。

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> 啟用或停用 Just My Code

針對大部分的程式設計語言，預設會啟用 Just My Code。

- 若要啟用或停用 Visual Studio 中的 Just My Code，請在 [**工具**  >  **選項**] (或 [**調試**  >  **選項**] 下) >   >  的 **[一般**]，選取 [**啟用 Just My Code**]。

![[選項] 對話方塊中的 [啟用 Just My Code]](../debugger/media/dbg_justmycode_options.png "啟用 Just My Code")

> [!NOTE]
> [**啟用 Just My Code** ] 是全域設定，適用于所有語言的所有 Visual Studio 專案。

## <a name="just-my-code-debugging"></a>Just My Code 偵錯

在偵錯工具中，[ **模組** ] 視窗會顯示偵錯工具視為 My Code (使用者程式碼) 以及其符號載入狀態的程式碼模組。 如需詳細資訊，請參閱 [深入瞭解偵錯工具附加至您應用程式的方式](../debugger/debugger-tips-and-tricks.md#modules_window)。

![[模組] 視窗中的使用者程式碼](../debugger/media/dbg_justmycode_module.png "[模組] 視窗中的使用者程式碼")

在 [ **呼叫堆疊** ] **或** [工作] 視窗中，Just My Code 折迭非使用者程式碼至標示為灰色的批註程式碼框架 `[External Code]` 。

![[呼叫堆疊] 視窗中的外部程式碼框架](../debugger/media/dbg_justmycode_externalcode.png "外部程式碼框架")

>[!TIP]
>若要開啟 [ **模組**]、[ **呼叫堆疊** **]、[** 工作] 或其他大部分的調試時間視窗，您必須在調試會話中。 進行調試時，在 [**調試** 時間]  >  **視窗** 中，選取您要開啟的視窗。

<a name="BKMK_Override_call_stack_filtering"></a> 若要查看折迭 **[外部程式碼]** 框架中的程式碼，請在 [ **呼叫堆疊** ] **或 [** 工作] 視窗中按一下滑鼠右鍵，然後從操作功能表中選取 [ **顯示外部程式碼** ]。 展開的外部程式程式碼會取代 **[外部程式碼**] 畫面格。

![在 [呼叫堆疊] 視窗中顯示外部程式碼](../debugger/media/dbg_justmycode_showexternalcode.png "顯示外部程式碼")

> [!NOTE]
> [**顯示外部程式碼**] 是目前的使用者 profiler 設定，適用于使用者所開啟之所有語言的所有專案。

按兩下 [ **呼叫堆疊** ] 視窗中展開的外部程式程式碼，會反白顯示原始程式碼中以綠色顯示的呼叫程式程式碼。 如果是找不到或無法載入 Dll 或其他模組，則可能會開啟 [找不到符號或來源] 頁面。

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Just My Code

在 .NET 專案中，Just My Code 使用符號 (*.pdb*) 檔案和程式優化，以分類使用者和非使用者程式碼。 .NET 偵錯工具會將優化的二進位檔和非載入的 *.pdb* 檔案視為非使用者程式碼。

三個編譯器屬性也會影響 .NET 偵錯工具視為使用者程式碼的內容：

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> 告知偵錯工具所套用的程式碼不是使用者程式碼。
- <xref:System.Diagnostics.DebuggerHiddenAttribute> 會對偵錯工具隱藏程式碼，即使 Just My Code 已關閉。
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> 告知偵錯工具逐步執行其套用的程式碼，而不是逐步執行程式碼。

.NET 偵錯工具會將所有其他程式碼視為使用者程式碼。

在 .NET 調試過程中：

- **Debug**  > **逐步** 執行 (或 **F11** ，將程式碼上的非使用者程式碼步驟) 到下一行使用者程式碼。
- **Debug**  > **跳出** (或 **Shift** + **F11**) 非使用者程式碼執行到下一行使用者程式碼。

如果沒有更多的使用者程式碼，則偵錯工具會繼續進行，直到它結束、到達另一個中斷點，或擲回錯誤。

<a name="BKMK_NET_Breakpoint_behavior"></a>如果偵錯工具在非使用者程式碼中中斷 (例如，您在  >  非使用者程式碼中使用 Debug **Break All** 和 pause) ，就不會出現 **任何來源** 視窗。 然後，您可以使用 **Debug**  >  **Step** 命令移至下一行使用者程式碼。

如果未處理的例外狀況發生在非使用者程式碼中，偵錯工具會在產生例外狀況的使用者程式程式碼上中斷。

如果例外狀況已啟用第一個可能的例外狀況，則會在原始程式碼中以綠色反白顯示呼叫的使用者程式碼。 [ **呼叫堆疊** ] 視窗會顯示標示為 **[外部程式碼]** 的標注框架。

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> C++ Just My Code

從 Visual Studio 2017 15.8 版開始，也支援適用于程式碼逐步執行的 Just My Code。 這項功能也需要使用 [/JMC (只) ](/cpp/build/reference/jmc) 編譯器參數的程式碼偵錯工具。 預設會在 c + + 專案中啟用參數。 如果是 Just My Code 中的 [ **呼叫堆疊** ] 視窗和 [呼叫堆疊] 支援，則不需要/JMC 參數。

<a name="BKMK_CPP_User_and_non_user_code"></a> 若要分類為使用者程式碼，偵錯工具必須載入包含使用者程式碼之二進位檔的 PDB (使用 [ **模組** ] 視窗檢查這個) 。

若為呼叫堆疊行為（例如在 [ **呼叫堆疊** ] 視窗中），則 c + + 中的 Just My Code 會將這些函式視為 *非使用者程式碼*：

- 在其符號檔中已移除來源資訊之函式。
- 符號檔表示沒有與堆疊框架對應的原始程式檔之函式。
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 資料夾中 *\* natjmc* 檔案所指定的函式。

針對程式碼逐步執行行為，c + + 中的 Just My Code 會將這些函數視為 *非使用者程式碼*：

- 的函式，其對應的 PDB 檔案尚未載入偵錯工具中。
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 資料夾中 *\* natjmc* 檔案所指定的函式。

> [!NOTE]
> 針對 Just My Code 中的程式碼逐步支援，您必須使用 Visual Studio 15.8 Preview 3 或更新版本中的 MSVC 編譯器來編譯 c + + 程式碼，而且必須啟用/JMC 編譯器參數 (預設會啟用) 。 如需其他詳細資訊，請參閱 [自訂 c + + 呼叫堆疊和程式碼逐步執行行為](#BKMK_CPP_Customize_call_stack_behavior)) 以及這 [篇 blog 文章](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)。 針對使用舊版編譯器編譯的程式碼， *natstepfilter* 檔案是自訂程式碼逐步執行的唯一方法，這與 Just My Code 無關。 請參閱 [自訂 c + + 逐步執行行為](#BKMK_CPP_Customize_stepping_behavior)。

<a name="BKMK_CPP_Stepping_behavior"></a> 在 c + + 調試期間：

- **Debug**  > **逐步** 執行 (或 **F11** ，將程式碼上的非使用者程式碼步驟) 到下一行使用者程式碼。
- **Debug**  > **跳出** (或 **Shift** + **F11**) 非使用者程式碼執行到下一行使用者程式碼。

如果沒有更多的使用者程式碼，則偵錯工具會繼續進行，直到它結束、到達另一個中斷點，或擲回錯誤。

如果偵錯工具在非使用者程式碼中中斷 (例如，您在  >  非使用者程式碼中使用 Debug **Break All** 和 pause) ，在非使用者程式碼中繼續執行。

如果偵錯工具遇到例外狀況，它會在例外狀況時停止，不論它是在使用者或非使用者程式碼中。 系統會忽略 [例外狀況 **設定**] 對話方塊中的 **使用者未處理** 選項。

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> 自訂 c + + 呼叫堆疊和程式碼逐步執行行為

針對 c + + 專案，您可以在 *\* natjmc* 檔案中指定模組、原始程式檔和函式 **，將其** 視為非使用者程式碼。 如果您使用的是最新編譯器 (請參閱 [c + + Just My Code](#BKMK_CPP_User_and_non_user_code)) ，此自訂也適用于程式碼逐步執行。

- 若要為 Visual Studio 電腦的所有使用者指定非使用者程式碼，請將 *natjmc* 檔案新增至 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 資料夾。
- 若要為個別使用者指定非使用者程式碼，請將 *natjmc* 檔案新增至 *%USERPROFILE%\My 檔 \\<Visual Studio 版本 \> \Visualizers* 資料夾。

*Natjmc* 檔案是具有下列語法的 XML 檔案：

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
|`Name`|必要。 該模組的完整路徑。 您可以使用 Windows 萬用字元 `?` (零或一個字元) 並 `*` (零或多個字元) 。 例如，<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 會告知偵錯工具中的所有模組都視為 *\3rdParty\UtilLibs* 為外部程式碼的任何磁碟機上。|
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

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> 自訂與 Just My Code 設定無關的 c + + 逐步執行行為

在 c + + 專案中，您可以將函式列為 *\* natstepfilter* 檔案中的非使用者程式碼，以指定要執行的函式。 *\* Natstepfilter* 檔案中所列的函式不會相依于 Just My Code 設定。

- 若要指定所有本機 Visual Studio 使用者的非使用者程式碼，請將 *natstepfilter* 檔案新增至 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 資料夾。
- 若要為個別使用者指定非使用者程式碼，請將 *natstepfilter* 檔案新增至 *%USERPROFILE%\My 檔 \\<Visual Studio 版本 \> \Visualizers* 資料夾。

*Natstepfilter* 檔案是具有下列語法的 XML 檔案：

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
|`Name`|必要。 指定要比對的完整函式名稱之 ECMA-262 格式化規則運算式。 例如：<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> 告知偵錯工具在 `MyNS::MyClass` 中的所有方法要視為非使用者程式碼。 該比對會區分大小寫。|
|`Module`|選擇性。 指定包含此函式的模組之完整路徑的 ECMA-262 格式化規則運算式。 該比對不區分大小寫。|
|`Action`|必要。 區分大小寫值的其中之一：<br /><br /> `NoStepInto`  -告訴偵錯工具不進入函數。<br /> `StepInto`  -告訴偵錯工具逐步執行函式，並覆寫比對函式的任何其他函式 `NoStepInto` 。|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript Just My Code

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript Just My Code 藉由將程式碼分類為下列其中一個分類，來控制逐步執行和呼叫堆疊顯示：

|分類|描述|
|-|-|
|**MyCode**|您所擁有並控制的使用者程式碼。|
|**LibraryCode**|您定期使用的程式庫中的非使用者程式碼，而您的應用程式會依賴正常運作 (例如 WinJS 或 jQuery) 。|
|**UnrelatedCode**|您應用程式中未擁有的非使用者程式碼，且您的應用程式不會依賴正常運作。 例如，可能會 UnrelatedCode 顯示廣告的廣告 SDK。 在 UWP 專案中，從 HTTP 或 HTTPS URI 載入至應用程式的任何程式碼也會被視為 UnrelatedCode。|

JavaScript 偵錯工具會依下列順序，將程式碼分類為使用者或非使用者：

1. 預設分類。
   - 藉由傳遞字串給主機提供的函式來執行的腳本 `eval` 是 **MyCode**。
   - 藉由將字串傳遞至函式來執行的腳本 `Function` 是 **LibraryCode**。
   - 架構參考中的腳本（例如 WinJS 或 Azure SDK）是 **LibraryCode**。
   - 藉由將字串傳遞至、或函式來執行的腳本 `setTimeout` `setImmediate` `setInterval` 是 **UnrelatedCode**。

2. 在檔案的 *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.js* 中，為所有 Visual Studio JavaScript 專案指定的分類。

3. 目前專案之檔案 *mycode.js* 的分類。

每個分類步驟都會覆寫先前的步驟。

所有其他程式碼會分類為 **MyCode**。

您可以修改預設分類，並將特定的檔案和 Url 分類為使用者或非使用者程式碼，方法是在 JavaScript 專案的根資料夾中新增名為 *mycode.js* 的 *json* 檔案。 請參閱 [自訂 JavaScript Just My Code](#BKMK_JS_Customize_Just_My_Code)。

<a name="BKMK_JS_Stepping_behavior"></a> 在 JavaScript 調試期間：

- 如果函式是非使用者程式碼，則 **調試** 程式  >  **逐步** 執行 (或 **F11**) 的行為會與  >  (或 **F10**) 上的 debug **步驟** 相同。
- 如果步驟在非使用者 (**LibraryCode** 或 **UnrelatedCode**) 程式碼中開始，則逐步執行的行為會如同 Just My Code 未啟用一樣。 當您逐步執行使用者程式碼時，Just My Code 逐步執行會重新啟用。
- 當使用者程式碼步驟導致離開目前的執行內容時，偵錯工具會在下一個執行的使用者程式程式碼上停止。 例如，如果回呼於 **LibraryCode** 程式碼中執行，則偵錯工具會繼續執行，直到下一行使用者程式碼執行為止。
- **跳出** (或 **Shift** + **F11**) 在下一行使用者程式碼停止。

如果沒有更多的使用者程式碼，則偵錯工具會繼續進行，直到它結束、到達另一個中斷點，或擲回錯誤。

系統一律會叫用在程式碼中設定的中斷點，但會分類程式代碼。

- 如果 `debugger` 關鍵字出現在 **LibraryCode** 中，偵錯工具一律會中斷。
- 如果 `debugger` 關鍵字發生在 **UnrelatedCode** 中，則偵錯工具不會停止。

<a name="BKMK_JS_Exception_behavior"></a> 如果 **MyCode** 或 **LibraryCode** 程式碼中發生未處理的例外狀況，則偵錯工具一律會中斷。

如果 **UnrelatedCode** 中發生未處理的例外狀況，而 **MyCode** 或 **LibraryCode** 是在呼叫堆疊上，則偵錯工具會中斷。

如果例外狀況已啟用第一個可能發生的例外狀況，則例外狀況會發生在 **LibraryCode** 或 **UnrelatedCode** 中：

- 如果已經處理此例外狀況，則偵錯工具不會中斷。
- 如果例外狀況未經處理，則偵錯工具會中斷。

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> 自訂 JavaScript Just My Code

若要分類單一 JavaScript 專案的使用者和非使用者程式碼，您可以將名為 *mycode.js* 的 *json* 檔案新增至專案的根資料夾。

此檔案中的規格會覆寫預設分類和檔案 *mycode.default.wwa.js* 。 檔案 *上的mycode.js* 不需要列出所有機碼值組。 **MyCode**、連結 **庫** 和不 **相關** 的值可以是空陣列。

檔案 *Mycode.js* 使用此語法：

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

|名稱|描述|
|-|-|
|**Eval**|藉由傳遞字串給主機所提供的 `eval` 函式來執行的指令碼。 根據預設，Eval 指令碼會分類為 **MyCode**。|
|**Function**|藉由傳遞字串給 `Function` 建構函式來執行的指令碼。 根據預設，Function 指令碼會分類為 **LibraryCode**。|
|**ScriptBlock**|由傳遞字串給 `setTimeout`、`setImmediate` 或 `setInterval` 函式所執行的指令碼。 根據預設，ScriptBlock 指令碼會分類為 **UnrelatedCode**。|

您可以變更此值為這些關鍵字之一：

- `MyCode` 將此指令碼分類為 **MyCode**。
- `Library` 將此指令碼分類為 **LibraryCode**。
- `Unrelated` 將此指令碼分類為 **UnrelatedCode**。

**MyCode、Libraries 和 Unrelated**

**MyCode**、**Libraries** 和 **Unrelated** 索引鍵值組會指定您在分類中要包含的 URL 或檔案：

|名稱|描述|
|-|-|
|**MyCode**|分類為 **MyCode** 的 URL 陣列或檔案陣列。|
|**程式庫**|分類為 **LibraryCode** 的 URL 陣列或檔案陣列。|
|**Unrelated**|分類為 **UnrelatedCode** 的 URL 陣列或檔案陣列。|

URL 或檔案字串可有一或多個 `*` 字元，以符合零或多個字元。 `*` 與正則運算式相同 `.*` 。
