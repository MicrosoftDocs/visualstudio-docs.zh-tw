---
title: 建立軟體開發套件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55b62ac0ac448023793f511389146ebb1b07da0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-software-development-kit"></a>建立軟體開發套件
軟體開發套件 (SDK) 是的 Api，您可以參考做為 Visual Studio 中的單一項目集合。 **參考管理員**對話方塊會列出與專案相關的所有 Sdk。 當您將 SDK 加入至專案時，應用程式開發介面是 Visual Studio 中提供。  
  
 有兩種類型的 Sdk:  
  
-   平台 Sdk 是開發平台的應用程式的必要元件。 例如， [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK，才能開發[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  
  
-   擴充功能 Sdk 會擴充平台，但不必要的開發平台的應用程式的選用元件。  
  
 下列章節描述一般的基礎結構的 Sdk，以及如何建立平台 SDK 和擴充功能 SDK。  
  
-   [平台 Sdk](#PlatformSDKs)  
  
-   [擴充功能 Sdk](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> 平台 Sdk  
 平台 Sdk，才能開發平台應用程式。 例如， [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK，才能開發的應用程式[!INCLUDE[win81](../debugger/includes/win81_md.md)]。  
  
### <a name="installation"></a>安裝  
 所有平台 Sdk 會安裝在 HKLM\Software\Microsoft\Microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK 根]。 因此， [!INCLUDE[win81](../debugger/includes/win81_md.md)] HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 在安裝 SDK。  
  
### <a name="layout"></a>配置  
 平台 Sdk 將會有下列配置：  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|節點|描述|  
|----------|-----------------|  
|[參考] 資料夾|包含二進位檔包含可以針對自動程式碼的 Api。 這些可能包括 Windows 中繼資料 (WinMD) 檔案或組件。|  
|DesignTime 資料夾|包含只能在前-run/偵錯期間所需的檔案。 這些可能包括 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等<br /><br /> XML 文件，在理想情況下，放在 \DesignTime 資料夾中，但 XML 文件的參考仍將會放置在一起的 Visual Studio 中的參考檔案。 例如，XML 文件的參考 \References\\[組態]\\[arch]\sample.dll 將 \References\\[組態]\\[arch]\sample.xml 和該文件的當地語系化的版本會 \References\\[組態]\\[架構]\\[locale]\sample.xml。|  
|設定資料夾|可以有只有三個資料夾： 偵錯、 零售和 CommonConfiguration。 如果同一組 SDK 檔案應該取用，不論目標 SDK 取用者的組態，SDK 作者可以放置在 CommonConfiguration 檔案。|  
|架構資料夾|可以存在的任何支援的架構資料夾。 Visual Studio 支援在下列架構： x86、 x64、 ARM 和 neutral。 注意： 為 x86，對應的 Win32 和 AnyCPU map 中性。<br /><br /> 平台 Sdk 下 \CommonConfiguration\neutral 只會尋找 MSBuild。|  
|SDKManifest.xml|此檔案描述 Visual Studio 應該如何使用 SDK。 在 SDK 資訊清單看起來[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** 物件瀏覽器會顯示在瀏覽清單中的值。<br /><br /> **PlatformIdentity:** 這個屬性的存在告知 Visual Studio 和 MSBuild 的 SDK 是平台 SDK 和從它所加入的參考，不應該複製在本機。<br /><br /> **TargetFramework:** 這個屬性可由 Visual Studio 來確保，只會目標相同的架構中的值所指定的專案屬性可能會耗用 SDK。<br /><br /> **MinVSVersion:** 這個屬性可由 Visual Studio 來使用套用至該 Sdk。<br /><br /> **參考：**這個屬性必須指定只包含控制項的參考。 如需如何指定參考是否包含控制項相關的資訊，請參閱下文。|  
  
##  <a name="ExtensionSDKs"></a> 擴充功能 Sdk  
 下列各節說明您需要如何部署擴充功能 SDK。  
  
### <a name="installation"></a>安裝  
 擴充功能 Sdk 可以針對特定的使用者或是針對所有使用者安裝未指定登錄機碼。 若要安裝的 SDK 給所有使用者，請使用下列路徑：  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 特定使用者安裝中，使用下列路徑：  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 如果您想要使用不同的位置，您必須執行下列任一步驟：  
  
1.  您可以指定它在登錄機碼：  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     新增的值為 （預設值） 子機碼和`<path to SDK><SDKName><SDKVersion>`。  
  
2.  將加入 MSBuild 屬性`SDKReferenceDirectoryRoot`專案檔。 這個屬性的值是半冒號分隔清單的位於您想要參考的擴充功能 Sdk 的目錄。  
  
### <a name="installation-layout"></a>安裝配置  
 擴充功能 Sdk 具有下列安裝配置：  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< s\>\\< SDKVersion\>： 名稱和版本的擴充功能 SDK SDK 根衍生自路徑中對應的資料夾名稱。 MSBuild 會使用這個身分識別在磁碟上，在此找到 SDK 及 Visual Studio 會顯示在這個身分識別**屬性**視窗和**參考管理員**對話方塊。  
  
2.  [參考] 資料夾： 包含應用程式開發介面的二進位檔。 這些可能是 Windows 中繼資料 (WinMD) 檔案或組件。  
  
3.  可轉散發套件的資料夾： 所需的執行階段/偵錯及應該做為使用者的應用程式的一部分取得封裝的檔案。 所有的二進位檔應該放下方 \redist\\< 組態\>\\< a c h\>，和二進位檔的名稱應該具有下列格式來確保唯一性： **\<公司 >。\<產品 >。\<用途 >。\<副檔名 >**。 例如，Microsoft.Cpp.Build.dll。 與其他 sdk （例如 javascript、 css、 pri、 xaml、 png 和 jpg 檔案） 的檔案名稱，可能會發生衝突名稱的所有檔案應該都放下方 \redist\\< 組態\>\\< a c h\> \\< s\>\ 與 XAML 相關聯的檔案除外控制。 這些檔案應該置於下方 \redist\\< 組態\>\\< a c h\>\\< componentname\>\\。  
  
4.  DesignTime 資料夾： 在只有前-run/偵錯所需的檔案時間與不應該被包裝成使用者的應用程式的一部分。 這些可能是 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等。 適用於原生專案的耗用量必須有任何 SDK *s*.props 檔案。 以下顯示此類型的檔案的範例。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML 參考文件被放置在一起的參考檔案。 例如，XML 參考文件 **\References\\< 組態\>\\< a c h\>\sample.dll**組件是 **\References\\< 組態\>\\< a c h\>\sample.xml**，和該文件的當地語系化的版本是 **\References\\< 組態\>\\<arch\>\\< 地區設定\>\sample.xml**。  
  
5.  設定資料夾： 三個子資料夾： 偵錯、 零售版和 CommonConfiguration。 同一組 SDK 檔案應該取用，不論目標 SDK 取用者的組態時，SDK 作者可以放置在 CommonConfiguration 檔案。  
  
6.  架構資料夾： 支援在下列架構： x86、 x64、 ARM、 中性。 Win32 對應為 x86，而 AnyCPU 對應到中性。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 此檔案描述 Visual Studio 應該如何使用 SDK。 下列為範例。  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 下列清單提供檔案的項目。  
  
1.  顯示名稱： 參考管理員、 方案總管、 物件瀏覽器，Visual Studio 使用者介面中的其他位置中出現的值。  
  
2.  ProductFamilyName： 整體 SDK 產品名稱。 例如， [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK 名為"Microsoft.WinJS.1.0"和"Microsoft.WinJS.2.0"，屬於相同系列的 SDK 產品系列，"Microsoft.WinJS"。 這個屬性可讓 Visual Studio 和 MSBuild 建立該連線。 如果這個屬性不存在，SDK 的名稱會做為產品系列名稱。  
  
3.  FrameworkIdentity： 指定這個屬性的值會放入取用應用程式資訊清單的一或多個 Windows 元件庫相依性。 這是屬性只適用於 Windows 的元件程式庫。  
  
4.  TargetFramework： 指定 [參考管理員] 與 [工具箱] 中可用的 Sdk。 這是以分號分隔清單的目標 framework moniker，例如 「.NET Framework，version = 2.0 版;.NET Framework，version = v4.5.1"。 如果指定了相同的目標架構的數個版本，參考管理員會使用指定的最低版本進行篩選。 例如，如果".NET Framework，version = v2.0;.NET Framework，version = v4.5.1"指定，則會使用參考管理員 「.NET Framework，version = v2.0"。 如果指定了特定的目標 framework 設定檔，該設定檔將會使用參考管理員進行篩選。 例如，當 「 Silverlight，版本 = v4.0，profile = WindowsPhone"指定，則篩選只在 Windows Phone 設定檔; 上的參考管理員完整的 Silverlight 4.0 Framework 為目標的專案不會看到在 [參考管理員] 中的 SDK。  
  
5.  MinVSVersion： 最小 Visual Studio 版本。  
  
6.  MaxPlatformVerson： 最大目標平台版本應該用來指定擴充功能 SDK 將無法運作所在的平台版本。 例如，Microsoft Visual c + + Runtime Package v11.0 應該只能由 Windows 8 專案參考。 因此，Windows 8 專案的 MaxPlatformVersion 為 8.0。 也就是說，針對 Windows 8.1 專案，參考管理員會篩選出 Microsoft Visual c + + Runtime Package，MSBuild 會擲回的錯誤時[!INCLUDE[win81](../debugger/includes/win81_md.md)]專案參考它。 注意： 這個項目開始便支援[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。  
  
7.  AppliesTo： 指定指定適用的 Visual Studio 專案類型都可以在 [參考管理員] 中的 Sdk。 會辨識九個值： WindowsAppContainer、 VisualC、 VB、 CSharp、 WindowsXAML、 JavaScript、 受管理，與原生。 SDK 作者可以使用和 ("+')，或 (「&#124;")，而非 ("！")若要指定完全 SDK 適用於專案類型的範圍運算子。  
  
     WindowsAppContainer 識別專案[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  
  
8.  SupportPrefer32Bit： 支援的值為"True"和"False"。 預設為"True"。 如果值設定為"False"時，MSBuild 會傳回錯誤，而[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]專案 （或傳統型專案中的警告） 如果參考的 SDK 專案具有 Prefer32Bit 啟用。 如需 Prefer32Bit 的詳細資訊，請參閱[建置 頁面，專案設計工具 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[編譯的頁面上，專案設計工具 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)。  
  
9. SupportedArchitectures： 以分號分隔的清單，此 SDK 支援的架構。 如果不支援目標的 SDK 架構中使用的專案，MSBuild 會顯示警告。 如果未指定此屬性，MSBuild 會永遠不會顯示這種類型的警告。  
  
10. SupportsMultipleVersions： 如果此屬性設為**錯誤**或**警告**，MSBuild 會表示相同的專案無法參考相同的 SDK 系列的多個版本。 如果這個屬性不存在，或設為**允許**，MSBuild 不會顯示這種類型的錯誤或警告。  
  
11. AppX： 指定磁碟上的 Windows 元件庫的應用程式套件的路徑。 在本機偵錯期間，這個值會傳給 Windows 元件庫的註冊元件。 檔案名稱的命名慣例是**\<公司 >。\<產品 >。\<架構 >。\<組態 >。\<版本 >.appx**。 如果它們不適用於 Windows 的元件程式庫，組態和架構是選擇性的屬性名稱和屬性值。 此值為僅適用於 Windows 的元件程式庫。  
  
12. CopyRedistToSubDirectory： 指定 \redist 資料夾下的檔案應可複製其中相對於應用程式封裝根目錄 (亦即**封裝位置**建立應用程式套件精靈中選擇) 和執行階段的配置根。 預設位置是在應用程式套件與 F5 配置的根目錄。  
  
13. DependsOn: SDK 識別定義此 SDK 所依賴的 Sdk 清單。 這個屬性會出現在詳細資料窗格的 參考管理員。  
  
14. MoreInfo： 提供說明和其他資訊的網頁 URL。 此值用於在 [參考管理員] 的右窗格中的其他相關資訊連結。  
  
15. 註冊類型： 指定 WinMD 註冊應用程式資訊清單中，而不需要為其對等項目的實作 DLL 中的原生 WinMD。  
  
16. 檔案參考： 指定包含控制項或原生 Winmd 這些參考。 如需如何指定參考是否包含控制項相關的資訊，請參閱[指定工具箱項目的位置](#ToolboxItems)下方。  
  
##  <a name="ToolboxItems"></a> 指定工具箱項目的位置  
 ToolBoxItems SDKManifest.xml 結構描述項目會指定平台和擴充功能 Sdk 中的類別和工具箱項目的位置。 下列範例會示範如何指定不同的位置。 這是適用於 WinMD 或 DLL 的參考。  
  
1.  將控制項放在 [工具箱] 的預設分類。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  將特定類別名稱下的控制項。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  放置在特定的類別名稱 底下的控制項。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Blend 與 Visual Studio 中放置在不同的類別名稱 底下的控制項。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  列舉特定控制項不同的 Blend 與 Visual Studio。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  列舉特定控制項，並將它們放在 Visual Studio 共用路徑，或只存在於所有的控制項群組。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  列舉特定控制項，並顯示 ChooseItems 未加上只有一組特定的工具箱中。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 建立使用 c + + SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說： 建立使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [管理專案中的參考](../ide/managing-references-in-a-project.md)