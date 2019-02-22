---
title: Vbc 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a4610f5603ad0197487c198074ad72d1381fda1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802185"
---
# <a name="vbc-task"></a>Vbc 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
包裝 vbc.exe，這會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 或程式碼模組 (.netmodule)。 如需 vbc.exe 的詳細資訊，請參閱 [Visual Basic 命令列編譯器](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)。  
  
## <a name="parameters"></a>參數  
 下表說明 `Vbc` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`AdditionalLibPaths`|選擇性的 `String[]` 參數。<br /><br /> 指定其他資料夾，在其中尋找參考屬性中指定的組件。|  
|`AddModules`|選擇性的 `String[]` 參數。<br /><br /> 讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。 此參數對應至 vbc.exe 編譯器的 [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) 參數。|  
|`BaseAddress`|選擇性的 `String` 參數。<br /><br /> 指定 DLL 的基底位址。 此參數對應至 vbc.exe 編譯器的 [/baseaddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) 參數。|  
|`CodePage`|選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 此參數對應至 vbc.exe 編譯器的 [/codepage](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) 參數。|  
|`DebugType`|選擇性的 `String[]` 參數。<br /><br /> 造成編譯器產生偵錯資訊。 此參數的值如下：<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 預設值為 `full`，可將偵錯工具附加至執行中的程式。 `pdbonly` 值可於偵錯工具中啟動程式時，讓原始程式碼進行偵錯，但只有當執行中的程式附加在偵錯工具時，才會顯示組合語言程式碼。 如需詳細資訊，請參閱 [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2)。|  
|`DefineConstants`|選擇性的 `String[]` 參數。<br /><br /> 定義條件式編譯器常數。 符號/值組會以分號分隔，並且使用下列語法指定：<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> 此參數對應至 vbc.exe 編譯器的 [/define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) 參數。|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會將公開金鑰放在組件中。 如為 `false`，工作會完整簽署組件。 預設值為 `false`。此參數除非搭配 `KeyFile` 參數或 `KeyContainer` 參數使用，否則沒有任何作用。 此參數對應至 vbc.exe 編譯器的 [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) 參數。|  
|`DisabledWarnings`|選擇性的 `String` 參數。<br /><br /> 隱藏指定的警告。 您只需要指定警告識別項的數值部分。 若有多個警告，則會以分號分隔。 此參數對應至 vbc.exe 編譯器的 [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) 參數。|  
|`DocumentationFile`|選擇性的 `String` 參數。<br /><br /> 將文件註解處理成指定的 XML 檔案。 此參數會覆寫 `GenerateDocumentation` 屬性。 如需詳細資訊，請參閱 [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65)。|  
|`EmitDebugInformation`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作就會產生偵錯資訊，並將其放在 .pdb 檔案中。 如需詳細資訊，請參閱 [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2)。|  
|`ErrorReport`|選擇性的 `String` 參數。<br /><br /> 指定工作應如何報告編譯器內部錯誤。 此參數的值如下：<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> 如果指定 `prompt` 且發生編譯器內部錯誤時，會提示使用者選擇是否將錯誤資料傳送給 Microsoft。<br /><br /> 如果指定 `send` 且發生編譯器內部錯誤時，工作會將錯誤資料傳送給 Microsoft。<br /><br /> 預設值為 `none`，僅報告文字輸出中的錯誤。<br /><br /> 此參數對應至 vbc.exe 編譯器的 [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) 參數。|  
|`FileAlignment`|選擇性的 `Int32` 參數。<br /><br /> 以位元組為單位，指定要對齊輸出檔案區段的位置。 此參數的值如下：<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> 此參數對應至 vbc.exe 編譯器的 [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) 參數。|  
|`GenerateDocumentation`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true` 則產生文件資訊，並將該資訊放入 XML 檔中，此檔案的名稱為工作所建立的可執行檔或程式庫名稱。 如需詳細資訊，請參閱 [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65)。|  
|`Imports`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 從指定的項目集合匯入命名空間。 此參數對應至 vbc.exe 編譯器的 [/imports](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) 參數。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 此參數對應至 vbc.exe 編譯器的 [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) 參數。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 如需詳細資訊，請參閱 [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8)。|  
|`LangVersion`|選擇性的 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) 參數。<br /><br /> 指定語言版本，"9" 或 "10"。|  
|`LinkResources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 .NET Framework 資源的連結；不要將資源檔放置於輸出檔中。 此參數對應至 vbc.exe 編譯器的 [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) 參數。|  
|`MainEntryPoint`|選擇性的 `String` 參數。<br /><br /> 指定包含 `Sub Main` 程序的類別或模組。 此參數對應至 vbc.exe 編譯器的 [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) 參數。|  
|`ModuleAssemblyName`|選擇性的 `String` 參數。<br /><br /> 指定將包含此模組的組件。|  
|`NoConfig`|選擇性的 `Boolean` 參數。<br /><br /> 指定編譯器不應使用 vbc.rsp 檔案。 此參數對應至 vbc.exe 編譯器的 [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) 參數。|  
|`NoLogo`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會隱藏顯示編譯器橫幅資訊。 此參數對應至 vbc.exe 編譯器的 [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) 參數。|  
|`NoStandardLib`|選擇性的 `Boolean` 參數。<br /><br /> 使編譯器不要參考標準程式庫。 此參數對應至 vbc.exe 編譯器的 [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) 參數。|  
|`NoVBRuntimeReference`|選擇性的 `Boolean` 參數。<br /><br /> 僅供內部使用。 如果為 true，則防止自動參考 Microsoft.VisualBasic.dll。|  
|`NoWarnings`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作便會隱藏所有警告。 如需詳細資訊，請參閱 [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)。|  
|`Optimize`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則啟用編譯器最佳化。 此參數對應至 vbc.exe 編譯器的 [/optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) 參數。|  
|`OptionCompare`|選擇性的 `String` 參數。<br /><br /> 指定如何進行字串比較。 此參數的值如下：<br /><br /> -   `binary`<br />-   `text`<br /><br /> 值 `binary` 指定此工作使用二進位字串比較。 值 `text` 指定此工作使用文字字串比較。 此參數的預設值為 `binary`。 此參數對應至 vbc.exe 編譯器的 [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) 參數。|  
|`OptionExplicit`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，則需要明確宣告變數。 此參數對應至 vbc.exe 編譯器的 [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) 參數。|  
|`OptionInfer`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，允許變數的類型推斷。|  
|`OptionStrict`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會強制執行嚴格的類型語意來限制隱含類型轉換。 此參數對應至 vbc.exe 編譯器的 [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) 參數。|  
|`OptionStrictType`|選擇性的 `String` 參數。<br /><br /> 指定哪些嚴格的類型語意會產生警告。 目前只支援 "custom"。 此參數對應至 vbc.exe 編譯器的 [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) 參數。|  
|`OutputAssembly`|選擇性的 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 這個參數對應於 vbc.exe 編譯器的 [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) 參數。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 這個參數可以具有 `x86`、`x64`、`Itanium` 或 `anycpu` 的值。 預設為 `anycpu`。 這個參數對應於 vbc.exe 編譯器的 [/platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) 參數。|  
|`References`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 導致工作將公用類型資訊從指定的項目匯入目前的專案。 這個參數對應於 vbc.exe 編譯器的 [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) 參數。|  
|`RemoveIntegerChecks`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，停用整數的溢位錯誤檢查。 預設值為 `false`。 這個參數對應於 vbc.exe 編譯器的 [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) 參數。|  
|`Resources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 .NET Framework 資源內嵌到輸出檔中。 這個參數對應於 vbc.exe 編譯器的 [/resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) 參數。|  
|`ResponseFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含適用於此工作之命令的回應檔。 此參數對應至 vbc.exe 編譯器的 [@ (指定回應檔)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) 選項。|  
|`RootNamespace`|選擇性的 `String` 參數。<br /><br /> 指定所有類型宣告的根命名空間。 這個參數對應於 vbc.exe 編譯器的 [/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) 參數。|  
|`SdkPath`|選擇性的 `String` 參數。<br /><br /> 指定 mscorlib.dll 和 microsoft.visualbasic.dll 的位置。 這個參數對應於 vbc.exe 編譯器的 [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) 參數。|  
|`Sources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 原始程式檔。|  
|`TargetCompactFramework`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，工作會以 [!INCLUDE[Compact](../includes/compact-md.md)] 為目標。 這個參數對應於 vbc.exe 編譯器的 [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) 參數。|  
|`TargetType`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 此參數的值如下：`library` (可建立程式碼程式庫)、`exe` (可建立主控台應用程式)、`module` (可建立模組) 或 `winexe` (可建立 Windows 程式)。 預設為 `library`。 這個參數對應於 vbc.exe 編譯器的 [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) 參數。|  
|`Timeout`|選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。|  
|`ToolPath`|選擇性的 `String` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔 (vbc.exe)。 如果未指定這個參數，工作會使用 SDK 安裝路徑，此路徑對應到執行 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 之架構的版本。|  
|`TreatWarningsAsErrors`|選擇性的 `Boolean` 參數。<br /><br /> 如為 `true`，所有警告都視為錯誤。 如需詳細資訊，請參閱 [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)。|  
|`UseHostCompilerIfAvailable`|選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，即會指示工作來使用同處理序編譯器物件。 僅可供 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用。|  
|`Utf8Output`|選擇性的 `Boolean` 參數。<br /><br /> 使用 UTF-8 編碼記錄編譯器輸出。 這個參數對應於 vbc.exe 編譯器的 [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) 參數。|  
|`Verbosity`|選擇性的 `String` 參數。<br /><br /> 指定編譯器輸出的詳細資訊。 詳細資訊可以是 `Quiet`、`Normal` (預設值) 或 `Verbose`。|  
|`WarningsAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)。<br /><br /> 此參數會覆寫 `TreatWarningsAsErrors` 參數。|  
|`WarningsNotAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)。<br /><br /> 唯有將 `TreatWarningsAsErrors` 參數設為 `true` 時，此參數才有用。|  
|`Win32Icon`|選擇性的 `String` 參數。<br /><br /> 在組件中插入 .ico 檔，讓輸出檔在 [檔案總管] 中具有所需的外觀。 這個參數對應於 vbc.exe 編譯器的 [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) 參數。|  
|`Win32Resources`|選擇性的 `String` 參數。<br /><br /> 將 Win32 資源檔 (.res) 插入輸出檔。 這個參數對應於 vbc.exe 編譯器的 [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) 參數。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會編譯 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 專案。  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic 命令列編譯器](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
