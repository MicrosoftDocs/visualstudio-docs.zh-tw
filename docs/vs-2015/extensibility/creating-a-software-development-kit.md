---
title: 建立軟體開發套件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acad28e365c70a89c50b77e141e428468b9a6df2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109786"
---
# <a name="creating-a-software-development-kit"></a>建立軟體開發套件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

軟體開發套件 (SDK) 是一系列 Api，您可以參考 Visual Studio 中的單一項目。 **參考管理員**對話方塊會列出所有與專案相關的 Sdk。 當您將 SDK 加入專案時，就有一個 Api 可在 Visual Studio 中。  
  
 有兩種類型的 Sdk:  
  
- 平台 Sdk 的開發平台的應用程式的必要元件。 例如， [!INCLUDE[win81](../includes/win81-md.md)] SDK，才能開發[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式。  
  
- 擴充功能 Sdk 是選擇性的元件擴充的平台，但不是開發應用程式，該平台的必要項目。  
  
  下列各節說明一般的基礎結構的 Sdk 以及如何建立平台 SDK 和擴充功能 SDK。  
  
- [平台 Sdk](#PlatformSDKs)  
  
- [擴充功能 Sdk](#ExtensionSDKs)  
  
## <a name="PlatformSDKs"></a> 平台 Sdk  
 平台 Sdk，才能開發平台的應用程式。 例如， [!INCLUDE[win81](../includes/win81-md.md)] SDK，才能開發的應用程式[!INCLUDE[win81](../includes/win81-md.md)]。  
  
### <a name="installation"></a>安裝  
 所有平台 Sdk 將會安裝在 HKLM\Software\Microsoft\Microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK 根]。 因此， [!INCLUDE[win81](../includes/win81-md.md)] HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 在已安裝的 SDK。  
  
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
|[參考] 資料夾|包含二進位檔，包含可以比照的 Api。 這些可能包括 Windows 中繼資料 (WinMD) 檔案或組件。|  
|DesignTime 資料夾|包含只能在後置入執行/偵錯階段所需的檔案。 這些可能是 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等<br /><br /> XML 文件，在理想情況下，放在 \DesignTime 資料夾中，但是參考的 XML 文件將會繼續被放置在一起的 Visual Studio 中的參考檔案。 例如，XML 文件的參考 \References\\[設定]\\[arch]\sample.dll 會 \References\\[config]\\[arch]\sample.xml 和，文件的當地語系化的版本會 \References\\[設定]\\[arch]\\[locale]\sample.xml。|  
|設定資料夾|可以有三個資料夾： 偵錯、 零售和 CommonConfiguration。 如果相同的 SDK 檔案集應該取用，不論 SDK 取用者會為目標的組態，SDK 作者可以放置在 CommonConfiguration 檔案。|  
|架構資料夾|可以存在的任何支援的架構資料夾。 Visual Studio 支援下列架構： x86、 x64、 ARM、 忍受及無感。 注意:Win32 對應設為 x86，而 AnyCPU 對應到中性。<br /><br /> MSBuild 會只有在 \CommonConfiguration\neutral 平台 Sdk。|  
|SDKManifest.xml|此檔案會描述 Visual Studio 應該如何使用 SDK。 在 SDK 資訊清單看起來[!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** 物件瀏覽器會顯示在瀏覽清單中的值。<br /><br /> **PlatformIdentity:** 此屬性存在本機告訴 Visual Studio 和 MSBuild SDK 是一個平台 SDK，而且不應該複製從它所加入的參考。<br /><br /> **TargetFramework:** Visual Studio 會使用此屬性以確保，只會為這個值指定相同的架構目標的專案屬性可使用 SDK。<br /><br /> **MinVSVersion:** Visual Studio 會使用這個屬性，使用套用至該 Sdk。<br /><br /> **參考：** 這個屬性必須指定只包含控制項的參考。 如需如何指定參考是否包含控制項相關的資訊，如下所示。|  
  
## <a name="ExtensionSDKs"></a> 擴充功能 Sdk  
 下列各節說明您需要如何部署擴充功能 SDK。  
  
### <a name="installation"></a>安裝  
 擴充功能 Sdk 可以針對特定的使用者或是針對所有使用者安裝但未指定登錄機碼。 若要安裝的 SDK 給所有使用者，請使用下列路徑：  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 使用者特定安裝中，使用下列路徑：  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 如果您想要使用不同的位置，您必須執行下列其中一種：  
  
1. 您可以指定它在登錄機碼：  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     並將其值為 （預設值） 子機碼`<path to SDK><SDKName><SDKVersion>`。  
  
2. 新增 MSBuild 屬性`SDKReferenceDirectoryRoot`至專案檔。 這個屬性的值是您想要參考的擴充功能 Sdk 所在的目錄半分號分隔清單。  
  
### <a name="installation-layout"></a>安裝版面配置  
 擴充功能 Sdk 有下列安裝版面配置：  
  
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
  
1. \\< SDKName\>\\< SDKVersion\>: SDK SDK 根目錄衍生自對應的資料夾名稱，在路徑中的延伸模組版本與名稱。 MSBuild 會使用這個身分識別在磁碟上，找到 SDK 和 Visual Studio 會顯示在此身分識別**屬性**視窗和**參考管理員**對話方塊。  
  
2. [參考] 資料夾： 包含 Api 的二進位檔。 這些可能是 Windows 中繼資料 (WinMD) 檔案或組件。  
  
3. 可轉散發套件資料夾： 所需的執行階段/偵錯，並應該取得使用者的應用程式的一部分一起封裝的檔案。 所有的二進位檔應該放下方 \redist\\< 組態\>\\< a c h\>，和二進位檔的名稱應該具有下列格式來確保唯一性： **\<公司 >。\<產品 >。\<目的 >。\<擴充功能 >**。 比方說，Microsoft.Cpp.Build.dll。 名稱可能會發生衝突與其他 sdk （例如 javascript、 css、 pri、 xaml、 png 和 jpg 檔案） 的檔案名稱的所有檔案都應放下方 \redist\\< 組態\>\\< a c h\> \\< sdkname\>\ 與 XAML 相關聯的檔案除外控制。 這些檔案都應放下方 \redist\\< 組態\>\\< a c h\>\\< componentname\>\\。  
  
4. DesignTime 資料夾： 在唯一後置入執行/偵錯所需的檔案時間和不應被包裝成使用者的應用程式的一部分。 這些可能是 XML 文件、 程式庫、 標頭、 工具箱設計階段二進位檔，MSBuild 成品等等。 適用於原生專案的耗用量必須要有的任何 SDK *SDKName*.props 檔案。 下面顯示的範例，這種類型的檔案。  
  
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
  
     XML 參考文件放在一起的參考檔案。 例如，XML 參考文件**\References\\< 組態\>\\< a c h\>\sample.dll**組件是**\References\\< 組態\>\\< a c h\>\sample.xml**，，文件的當地語系化的版本，而且**\References\\< 組態\>\\<arch\>\\< 地區設定\>\sample.xml**。  
  
5. 設定資料夾： 三個子資料夾：偵錯、 零售版和 CommonConfiguration。 相同的 SDK 檔案集應該取用，不論目標 SDK 取用者的組態時，SDK 作者可以放置在 CommonConfiguration 檔案。  
  
6. 架構資料夾： 支援下列架構： x86、 x64、 ARM、 中性。 Win32 對應設為 x86，而 AnyCPU 對應到中性。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 此檔案會描述 Visual Studio 應該如何使用 SDK。 下列為範例。  
  
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
  
1. DisplayName： 參考管理員、 方案總管 中，物件瀏覽器，Visual Studio 使用者介面中的其他位置中出現的值。  
  
2. ProductFamilyName:整體的 SDK 產品名稱。 比方說， [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK 名為"Microsoft.WinJS.1.0 」 和 「 Microsoft.WinJS.2.0"，屬於相同系列的 SDK 產品系列，「 Microsoft.WinJS"。 此屬性可讓 Visual Studio 和 MSBuild 來建立連線。 如果這個屬性不存在，則 SDK 名稱會使用為產品系列名稱。  
  
3. FrameworkIdentity： 指定此屬性的值會放入使用的應用程式資訊清單的一個或多個 Windows 元件庫相依性。 這個屬性是僅適用於 Windows 的元件程式庫。  
  
4. TargetFramework： 指定參考管理員] 和 [工具箱中可用的 Sdk。 這是以分號分隔清單的目標 framework moniker，例如 「.NET Framework，版本 = v2.0;.NET Framework，版本 = v4.5.1"。 如果指定了數個相同的目標 framework 版本，參考管理員會使用指定的最低版本進行篩選。 比方說，如果".NET Framework，版本 = v2.0;.NET Framework、 版本 = v4.5.1"指定，則會使用參考管理員 「.NET Framework、 版本 = v2.0"。 如果指定了特定的目標 framework 設定檔，該設定檔將用於參考管理員進行篩選。 例如，當 「 Silverlight，版本 = v4.0，設定檔 = WindowsPhone"指定，則參考管理員篩選僅 Windows Phone 設定檔;以完整的 Silverlight 4.0 Framework 為目標的專案不會看到在參考管理員 中的 SDK。  
  
5. MinVSVersion： 最小 Visual Studio 版本。  
  
6. MaxPlatformVerson:最大的目標平台版本應該用於指定擴充功能 SDK 將無法運作所在的平台版本。 例如，Microsoft 視覺效果C++執行階段套件 v11.0 應只由 Windows 8 專案參考。 因此，Windows 8 專案的 MaxPlatformVersion 為 8.0。 這表示參考管理員篩選出 Microsoft VisualC++執行階段套件，針對 Windows 8.1 專案，因此 MSBuild 會擲回錯誤時[!INCLUDE[win81](../includes/win81-md.md)]專案會參考它。 注意： 這個項目從開始支援[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]。  
  
7. AppliesTo： 指定藉由指定適用的 Visual Studio 專案類型會在參考管理員 中可用的 Sdk。 辨識九個值：WindowsAppContainer、 VisualC、 VB、 CSharp、 WindowsXAML、 管理、 JavaScript 和原生。 SDK 撰寫者可以使用和 ("+')，或 (「&#124;")，而非 ("！")若要指定完全適用於 SDK 的專案類型的範圍運算子。  
  
     WindowsAppContainer 識別專案[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式。  
  
8. SupportPrefer32Bit:支援的值為"True"和"False"。 預設值為"True"。 如果值設定為"False"時，MSBuild 會傳回的錯誤[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]專案 （或警告對於傳統型專案） 如果參考 SDK 的專案已啟用的 Prefer32Bit。 如需 Prefer32Bit 的詳細資訊，請參閱[建置 Page，Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md)或是[編譯的 Page，Project Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)。  
  
9. SupportedArchitectures： 以分號分隔的清單的 SDK 支援的架構。 如果不支援目標的 SDK 架構中使用的專案，MSBuild 就會顯示警告。 如果未指定此屬性，MSBuild 會永遠不會顯示這種類型的警告。  
  
10. SupportsMultipleVersions： 如果此屬性設為**錯誤**或是**警告**，MSBuild 表示相同的專案無法參考多個版本的相同 SDK 系列產品。 如果這個屬性不存在，或設為**允許**，MSBuild 不會顯示這種類型的錯誤或警告。  
  
11. AppX： 指定在磁碟上的 Windows 元件程式庫的應用程式套件的路徑。 在本機偵錯期間，這個值會傳遞至 Windows 元件程式庫的註冊元件。 檔案名稱的命名慣例是**\<公司 >。\<產品 >。\<架構 >。\<組態 >。\<版本 >.appx**。 如果它們不適用於 Windows 的元件程式庫，設定與架構是選擇性的屬性名稱和屬性值。 這個值是僅適用於 Windows 的元件程式庫。  
  
12. CopyRedistToSubDirectory： 指定在 \redist 資料夾下的檔案複製目的地相對於應用程式封裝根目錄 (亦即**封裝位置**選擇建立應用程式套件精靈 中) 和執行階段配置根。 預設位置是根的應用程式封裝和 F5 版面配置。  
  
13. DependsOn:定義此 SDK 所依賴之 Sdk 的 SDK 身分識別清單。 這個屬性會出現在 [參考管理員] 的詳細資料窗格中。  
  
14. MoreInfo： 提供說明和詳細資訊的網頁 URL。 這個值會在右窗格的 [參考管理員中的詳細資訊] 連結。  
  
15. 註冊類型： 指定 WinMD 註冊應用程式資訊清單中，而且需要有對應實作 DLL 中的原生 WinMD。  
  
16. 檔案參考： 指定只包含控制項或原生 Winmd 這些參考。 如需有關如何指定參考是否包含控制項的資訊，請參閱[指定位置的工具箱項目的](#ToolboxItems)如下。  
  
## <a name="ToolboxItems"></a> 指定工具箱項目的位置  
 ToolBoxItems SDKManifest.xml 結構描述項目會指定平台和擴充功能 Sdk 中的類別目錄和工具箱項目的位置。 下列範例示範如何指定不同的位置。 這是適用於 WinMD 或 DLL 的參考。  
  
1. 將控制項放在 [工具箱] 的預設分類。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2. 將特定類別名稱的控制項。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3. 放置在特定的類別名稱 底下的控制項。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4. 在 Blend 和 Visual Studio 中放置在不同的類別名稱 底下的控制項。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5. 列舉以不同的方式在 Blend 和 Visual Studio 中的特定控制項。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6. 列舉特定的控制項，並將它們放在 Visual Studio 共用路徑，或僅在所有的控制項群組。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7. 列舉特定控制項，並顯示只有一組特定 ChooseItems 中，而不需要它們要在工具箱中。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 SDK 建立C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說：使用 SDK 建立C#或 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [管理專案中的參考](../ide/managing-references-in-a-project.md)
