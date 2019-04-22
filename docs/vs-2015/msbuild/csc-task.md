---
title: Csc 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d69d19e43ae2e94382e32ba6579f55cecb2efca
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659480"
---
# <a name="csc-task"></a>Csc 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包裝 CSC.exe，並產生可執行檔 (.exe 檔)、動態連結程式庫 (.dll 檔) 或程式碼模組 (.netmodule 檔)。 如需 CSC.exe 的詳細資訊，請參閱 [C# 編譯器選項](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)。  
  
## <a name="parameters"></a>參數  
 下表說明 `Csc` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`AdditionalLibPaths`|選擇性的 `String[]` 參數。<br /><br /> 指定要搜尋參考的其他目錄。 如需詳細資訊，請參閱 [/lib (C# 編譯器選項)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673)。|  
|`AddModules`|選擇性的 `String` 參數。<br /><br /> 指定要成為組件一部分的一個或多個模組。 如需詳細資訊，請參閱 [/addmodule (C# 編譯器選項)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58)。|  
|`AllowUnsafeBlocks`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會編譯使用 [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) 關鍵字的程式碼。 如需詳細資訊，請參閱 [/unsafe (C# 編譯器選項)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc)。|  
|`ApplicationConfiguration`|選擇性的 `String` 參數。<br /><br /> 指定包含組件繫結設定的應用程式組態檔。|  
|`BaseAddress`|選擇性的 `String` 參數。<br /><br /> 指定載入 DLL 時慣用的基底位址。 DLL 的預設基底位址是由 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 通用語言執行平台所設定。 如需詳細資訊，請參閱 [/baseaddress (C# 編譯器選項)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608)。|  
|`CheckForOverflowUnderflow`|選擇性的 `Boolean` 參數。<br /><br /> 指定超出資料類型範圍的整數算術，是否會導致在執行階段發生例外狀況。 如需詳細資訊，請參閱 [/checked (C# 編譯器選項)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b)。|  
|`CodePage`|選擇性的 `Int32` 參數。<br /><br /> 指定編譯過程中所有原始程式碼檔使用的字碼頁。 如需詳細資訊，請參閱 [/codepage (C# 編譯器選項)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478)。|  
|`DebugType`|選擇性的 `String` 參數。<br /><br /> 指定偵錯類型。 `DebugType` 可以是 `full` 或 `pdbonly`。 預設值是 `full`，會將偵錯工具附加至執行中的程式。 指定 `pdbonly`，讓原始程式碼在偵錯工具中啟動程式時進行偵錯，但只有在將執行中的程式附加到偵錯工具時，才會顯示組譯工具。<br /><br /> 此參數會覆寫 `EmitDebugInformation` 參數。<br /><br /> 如需詳細資訊，請參閱 [/debug (C# 編譯器選項)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969)。|  
|`DefineConstants`|選擇性的 `String` 參數。<br /><br /> 定義前置處理器符號。 如需詳細資訊，請參閱 [/define (C# 編譯器選項)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e)。|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即表示您想要完整的簽署組件。 如果是 `false`，則表示您只想將公開金鑰放置於組件中。<br /><br /> 除非與 `KeyFile` 或 `KeyContainer` 參數搭配使用，否則此參數沒有任何作用。<br /><br /> 如需詳細資訊，請參閱 [/delaysign (C# 編譯器選項)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75)。|  
|`DisabledWarnings`|選擇性的 `String` 參數。<br /><br /> 指定要停用的警告清單。 如需詳細資訊，請參閱 [/nowarn (C# 編譯器選項)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4)。|  
|`DocumentationFile`|選擇性的 `String` 參數。<br /><br /> 將文件註解處理成 XML 檔案。 如需詳細資訊，請參閱 [/doc (C# 編譯器選項)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a)。|  
|`EmitDebugInformation`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，工作就會產生偵錯資訊，並將其放在程式資料庫 (.pdb) 檔案中。 如果是 `false`，工作就不會發出任何偵錯資訊。 預設為 `false`。 如需詳細資訊，請參閱 [/debug (C# 編譯器選項)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969)。|  
|`ErrorReport`|選擇性的 `String` 參數。<br /><br /> 提供將 C# 內部錯誤回報給 Microsoft 的便利方式。 此參數可以具有 `prompt`、`send` 或 `none` 的值。 如果將此參數設為 `prompt`，您將會在編譯器內部錯誤發生時收到提示。 此提示可讓您以電子方式將錯誤報告傳送給 Microsoft。 如果將此參數設為 `send`，就會自動傳送錯誤報告。 如果將此參數設為 `none`，則只會在編譯器的文字輸出中報告錯誤。 預設為 `none`。 如需詳細資訊，請參閱 [/errorreport (C# 編譯器選項)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf)。|  
|`FileAlignment`|選擇性的 `Int32` 參數。<br /><br /> 指定輸出檔案中區段的大小。 如需詳細資訊，請參閱 [/filealign (C# 編譯器選項)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073)。|  
|`GenerateFullPaths`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會在編譯器輸出中指定檔案的絕對路徑。 如果是 `false`，則會指定檔案的名稱。 預設為 `false`。 如需詳細資訊，請參閱 [/fullpaths (C# 編譯器選項)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4)。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定密碼編譯金鑰容器的名稱。 如需詳細資訊，請參閱 [/keycontainer (C# 編譯器選項)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763)。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定包含密碼編譯金鑰的檔名。 如需詳細資訊，請參閱 [/keyfile (C# 編譯器選項)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2)。|  
|`LangVersion`|選擇性的 `String` 參數。<br /><br /> 指定要使用的語言版本。 如需詳細資訊，請參閱 [/langversion (C# 編譯器選項)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94)。|  
|`LinkResources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 在輸出檔中建立 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 資源的連結；不要將資源檔放置於輸出檔中。<br /><br /> 傳遞到此參數的項目可以具備名為 `LogicalName` 和 `Access` 的選擇性中繼資料項目。 `LogicalName` 會對應至 `/linkresource` 參數 (Switch) 的 `identifier` 參數 (Parameter)，而 `Access` 會對應至 `accessibility-modifier` 參數 (Parameter)。 如需詳細資訊，請參閱 [/linkresource (C# 編譯器選項)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96)。|  
|`MainEntryPoint`|選擇性的 `String` 參數。<br /><br /> 指定 `Main` 方法的位置。 如需詳細資訊，請參閱 [/main (C# 編譯器選項)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049)。|  
|`ModuleAssemblyName`|選擇性的 `String` 參數。<br /><br /> 指定將包含此模組的組件名稱。|  
|`NoConfig`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會指示編譯器不要使用 csc.rsp 檔案進行編譯。 如需詳細資訊，請參閱 [/noconfig (C# 編譯器選項)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e)。|  
|`NoLogo`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會隱藏顯示編譯器橫幅資訊。 如需詳細資訊，請參閱 [/nologo (C# 編譯器選項)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c)。|  
|`NoStandardLib`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會防止匯入 mscorlib.dll，此檔案會定義整個系統命名空間。 如果您想要定義或建立自己的系統命名空間和物件，請使用此參數。 如需詳細資訊，請參閱 [/nostdlib (C# 編譯器選項)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f)。|  
|`NoWin32Manifest`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，就不會包含預設的 Win32 資訊清單。|  
|`Optimize`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會啟用最佳化。 如果是 `false`，則會停用最佳化。 如需詳細資訊，請參閱 [/optimize (C# 編譯器選項)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0)。|  
|`OutputAssembly`|選擇性的 `String` 輸出參數。<br /><br /> 指定輸出檔案的名稱。 如需詳細資訊，請參閱 [/out (C# 編譯器選項)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5)。|  
|`PdbFile`|選擇性的 `String` 參數。<br /><br /> 指定偵錯資訊檔案名稱。 預設名稱是副檔名為 .pdb 的輸出檔案名稱。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔設為目標的處理器平台。 此參數可以具有 `x86`、`x64` 或 `anycpu` 的值。 預設為 `anycpu`。 如需詳細資訊，請參閱 [/platform (C# 編譯器選項)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)。|  
|`References`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 導致工作將公用類型資訊從指定的項目匯入目前的專案。 如需詳細資訊，請參閱 [/reference (C# 編譯器選項)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4)。<br /><br /> 您可以將中繼資料 `Aliases` 加入至原始的「參考」項目，藉以在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 檔案中指定 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 參考別名。 例如，若要在下列 CSC 命令列中設定別名 "LS1"：<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> 您可以使用：<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 將 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 資源內嵌到輸出檔中。<br /><br /> 傳遞到此參數的項目可以具備名為 `LogicalName` 和 `Access` 的選擇性中繼資料項目。 `LogicalName` 會對應至 `/resource` 參數 (Switch) 的 `identifier` 參數 (Parameter)，而 `Access` 會對應至 `accessibility-modifier` 參數 (Parameter)。 如需詳細資訊，請參閱 [/resource (C# 編譯器選項)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f)。|  
|`ResponseFiles`|選擇性的 `String` 參數。<br /><br /> 指定包含適用於此工作之命令的回應檔。 如需詳細資訊，請參閱 [@ (指定回應檔)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f)。|  
|`Sources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 原始程式檔。|  
|`TargetType`|選擇性的 `String` 參數。<br /><br /> 指定輸出檔的檔案格式。 此參數的值如下：`library` (可建立程式碼程式庫)、`exe` (可建立主控台應用程式)、`module` (可建立模組) 或 `winexe` (可建立 Windows 程式)。 預設值為 `library`。 如需詳細資訊，請參閱 [/target (C# 編譯器選項)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f)。|  
|`TreatWarningsAsErrors`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會將所有警告視為錯誤。 如需詳細資訊，請參閱 [/warnaserror (C# 編譯器選項)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c)。|  
|`UseHostCompilerIfAvailable`|選擇性的 `Boolean` 參數。<br /><br /> 如果有的話，即會指示工作來使用同處理序編譯器物件。 僅可供 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用。|  
|`Utf8Output`|選擇性的 `Boolean` 參數。<br /><br /> 使用 UTF-8 編碼記錄編譯器輸出。 如需詳細資訊，請參閱 [/utf8output (C# 編譯器選項)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e)。|  
|`WarningLevel`|選擇性的 `Int32` 參數。<br /><br /> 指定要針對編譯器顯示的警告層級。 如需詳細資訊，請參閱 [/warn (C# 編譯器選項)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71)。|  
|`WarningsAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror (C# 編譯器選項)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c)。<br /><br /> 此參數會覆寫 `TreatWarningsAsErrors` 參數。|  
|`WarningsNotAsErrors`|選擇性的 `String` 參數。<br /><br /> 指定不要視為錯誤的警告清單。 如需詳細資訊，請參閱 [/warnaserror (C# 編譯器選項)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c)。<br /><br /> 唯有將 `TreatWarningsAsErrors` 參數設為 `true` 時，此參數才有用。|  
|`Win32Icon`|選擇性的 `String` 參數。<br /><br /> 在組件中插入 .ico 檔，讓輸出檔在 [檔案總管] 中具有所需的外觀。 如需詳細資訊，請參閱 [/win32icon (C# 編譯器選項)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)。|  
|`Win32Manifest`|選擇性的 `String` 參數。<br /><br /> 指定要包含的 Win32 資訊清單。|  
|`Win32Resource`|選擇性的 `String` 參數。<br /><br /> 將 Win32 資源檔 (.res) 插入輸出檔。 如需詳細資訊，請參閱 [/win32res (C# 編譯器選項)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b)。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 `Microsoft.Build.Tasks.ManagedCompiler` 類別中的參數，此類別繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別，而後者本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Csc` 工作，在 `Compile` 項目集合中從原始程式檔編譯可執行檔。  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)
