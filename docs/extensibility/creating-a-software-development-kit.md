---
title: 建立軟體發展工具組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 042002b6fddb674c0f1c156be2d992cc96cb9f81
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787673"
---
# <a name="create-a-software-development-kit"></a>建立軟體發展工具組

軟體發展工具組 (SDK) 是 Api 的集合, 您可以在 Visual Studio 中將其視為單一專案來參考。 [**參考管理員**] 對話方塊會列出與專案相關的所有 sdk。 當您將 SDK 新增至專案時, 會在 Visual Studio 中提供 Api。

Sdk 有兩種類型:

- 平臺 Sdk 是針對平臺開發應用程式的必要元件。 例如, [!INCLUDE[win81](../debugger/includes/win81_md.md)]需要 SDK 才能開發[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。

- 延伸模組 Sdk 是擴充平臺的選擇性元件, 但對於開發該平臺的應用程式並不是必要的。

下列各節說明 Sdk 的一般基礎結構, 以及如何建立平臺 SDK 和擴充功能 SDK。

## <a name="platform-sdks"></a>平臺 Sdk

需要平臺 Sdk, 才能開發平臺的應用程式。 例如, 需要[!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK, 才能開發的[!INCLUDE[win81](../debugger/includes/win81_md.md)]應用程式。

### <a name="installation"></a>安裝

所有平臺 sdk 都會安裝在*HKLM\Software\Microsoft\Microsoft\\sdk [TPI] \v [TPV]\\ @InstallationFolder = [SDK 根目錄]* 。 因此, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK 會安裝在*HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*。

### <a name="layout"></a>配置

平臺 Sdk 具有下列版面配置:

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

| 節點 | 說明 |
|------------------------| - |
| *參考*資料夾 | 包含二進位檔, 其中包含可針對進行編碼的 Api。 這些可能包括 Windows 中繼資料 (WinMD) 檔案或元件。 |
| *DesignTime*資料夾 | 包含只有在預執行/偵測時才需要的檔案。 這些可能包括 XML 檔、文件庫、標頭、工具箱設計階段二進位檔、MSBuild 成品等等<br /><br /> XML 檔在理想的情況下, 會放在 *\DesignTime*資料夾中, 但參考的 XML 檔會繼續放在 Visual Studio 中的參考檔案旁邊。 例如, 參考<em>\References\\[config]\\[\sample.dll</em> ] 的 XML 檔將會是 *\References\\[config]\\[* ] \sample.xml, 而該檔的當地語系化版本將會是 *\\\References\\[config]\\[架構] [地區設定] \sample.xml*。 |
| 設定資料夾 | 只能有三個資料夾:*Debug*、 *Retail*和*CommonConfiguration*。 SDK 作者可以將其檔案放在*CommonConfiguration*之下 (如果應該取用相同的 sdk 檔案集), 不論 sdk 取用者的目標設定為何。 |
| *架構*資料夾 | 任何支援的*架構*資料夾都可以存在。 Visual Studio 支援下列架構: x86、x64、ARM 和中性。 注意:Win32 對應至 x86, 而 AnyCPU 對應至中性。<br /><br /> MSBuild 只會查看平臺 Sdk 的 *\CommonConfiguration\neutral* 。 |
| *SDKManifest.xml* | 此檔案描述 Visual Studio 應該如何使用 SDK。 查看適用[!INCLUDE[win81](../debugger/includes/win81_md.md)]于的 SDK 資訊清單:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName：** 物件瀏覽器在瀏覽清單中顯示的值。<br /><br /> **PlatformIdentity:** 這個屬性的存在會告訴 Visual Studio 和 MSBuild, SDK 是平臺 SDK, 而從它新增的參考則不應該複製到本機。<br /><br /> **TargetFramework**Visual Studio 使用這個屬性, 以確保只有以這個屬性的值所指定之相同架構為目標的專案可以使用 SDK。<br /><br /> **MinVSVersion:** 此屬性是由 Visual Studio 用來只使用適用于它的 Sdk。<br /><br /> **證明**這個屬性必須僅針對包含控制項的參考指定。 如需如何指定參考是否包含控制項的詳細資訊, 請參閱下面的。 |

## <a name="extension-sdks"></a>延伸模組 Sdk

下列各節說明部署擴充功能 SDK 所需執行的動作。

### <a name="installation"></a>安裝

您可以為特定使用者或所有使用者安裝延伸模組 Sdk, 而不需要指定登錄機碼。 若要為所有使用者安裝 SDK, 請使用下列路徑:

*% Program Files%\Microsoft sdk\<目標平臺\>\v < 平臺版本號碼\>\ExtensionSDKs*

若為使用者特定安裝, 請使用下列路徑:

*%USERPROFILE%\AppData\Local\Microsoft sdk\<目標平臺\>\v < 平臺版本號碼\>\ExtensionSDKs*

如果您想要使用不同的位置, 您必須執行下列其中一項動作:

1. 在登錄機碼中指定它:

     **HKLM\Software\Microsoft\Microsoft sdk\<目標平臺 > \v < 平臺版本號碼\>\ExtensionSDKs\<SDKName >\<SDKVersion >** \

     並新增具有值的`<path to SDK><SDKName><SDKVersion>`(預設) 子機碼。

2. 將 MSBuild 屬性`SDKReferenceDirectoryRoot`加入至您的專案檔。 這個屬性的值是以分號分隔的目錄清單, 其中包含您想要參考的延伸模組 Sdk。

### <a name="installation-layout"></a>安裝版面配置

延伸模組 Sdk 具有下列安裝版面配置:

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

1. \\< SDKName\> \\<SDKVersion\>: 延伸模組 SDK 的名稱和版本衍生自 SDK 根目錄路徑中對應的資料夾名稱。 MSBuild 會使用此識別在磁片上尋找 SDK, Visual Studio 會在 [**屬性**] 視窗和 [**參考管理員**] 對話方塊中顯示此身分識別。

2. *References*資料夾: 包含 api 的二進位檔。 這些可能是 Windows 中繼資料 (WinMD) 檔案或元件。

3. 可轉散發資料夾: 執行時間/偵測所需的檔案, 而且應封裝為使用者應用程式的一部分。 所有的二進位檔都應該放在 *\redist\> \\<\>config\\<* 架構底下, 而且二進位檔名稱應具有下列格式, 以確保唯一性: *]* \<公司>。\<產品 >。\<目的 >。延伸模組<em>>。 \<例如, * Microsoft .Cpp</em>。 名稱與其他 sdk (例如 javascript、css、pri、xaml、png 和 jpg 檔案) 相衝突的所有檔案, 都<em>應該放在 \redist\\< config\> \\<\>架構底下< sdkname,但\>與 XAML 控制項相關聯的檔案除外。\* \\這些檔案應該放在 * \redist\\< config\> \\ \> \\ \>< 架構底下 < componentname\\</em> 。

4. *DesignTime*資料夾: 只在預執行/偵測時才需要的檔案, 不應封裝為使用者應用程式的一部分。 這些可能是 XML 檔、文件庫、標頭、工具箱設計階段二進位檔、MSBuild 成品等等。 任何要由原生專案取用的 SDK 都必須有*SDKName .props*檔案。 以下顯示這種檔案類型的範例。

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

    XML 參考檔會連同參考檔案一起放置在一起。 例如，XML 參考文件 *\References\\<組態\>\\<a c h\>\sample.dll*組件是 *\References\\<組態\>\\<a c h\>\sample.xml*，，文件的當地語系化的版本，而且 *\References\\<組態\>\\<arch\>\\< 地區設定\>\sample.xml*。

5. 設定資料夾: 三個子資料夾:*Debug*、 *Retail*和*CommonConfiguration*。 不論 SDK 取用者的目標設定為何, SDK 作者都可以將其檔案放在*CommonConfiguration*之下。

6. *架構*資料夾: 支援下列架構: x86、X64、ARM、中立。 Win32 對應至 x86, 而 AnyCPU 對應至中性。

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*Sdkmanifest.xml*會描述 Visual Studio 應該如何使用 SDK。 以下是一個範例：

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
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

下列清單提供檔案的元素:

1. DisplayName: 在 [參考管理員]、[方案總管]、[物件瀏覽器] 和 Visual Studio 的使用者介面中的其他位置中出現的值。

2. ProductFamilyName:整體 SDK 產品名稱。 例如, sdk 的[!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)]名稱為 "WinJS" 和 "WinJS. 2.0", 屬於相同的 SDK 產品系列 "microsoft. WinJS"。 這個屬性可讓 Visual Studio 和 MSBuild 進行該連接。 如果此屬性不存在, 則會使用 SDK 名稱做為產品系列名稱。

3. FrameworkIdentity指定一或多個 Windows 元件程式庫的相依性。 這個屬性的值會放入取用應用程式的資訊清單中。 此屬性僅適用于 Windows 元件程式庫。

4. TargetFramework指定可在 [參考管理員] 和 [工具箱] 中使用的 Sdk。 這是以分號分隔的目標 framework 名字清單, 例如 ".NET Framework, version = v2.0; .NET Framework, version = v4.0"。 如果指定了多個版本的相同目標架構, 則參考管理員會使用最低的指定版本來進行篩選。 例如, 如果指定了 ".NET Framework, version = v2.0; .NET Framework, version = v4.0", 則參考管理員會使用 ".NET Framework, version = v2.0"。 如果指定了特定的目標 framework 設定檔, 參考管理員就只會使用該設定檔進行篩選。 例如, 當指定了 "Silverlight, version = v4.0, profile = .Windows 及 .windowsphone" 時, 參考管理員只會篩選 Windows Phone 設定檔;以完整 Silverlight 4.0 架構為目標的專案, 在參考管理員中看不到 SDK。

5. MinVSVersion:Visual Studio 版本的最小值。

6. MaxPlatformVerson:目標平臺的最大版本應該用來指定您的擴充功能 SDK 將無法使用的平臺版本。 例如, Microsoft Visual C++ Runtime Package v 11.0 只能由 Windows 8 專案參考。 因此, Windows 8 專案的 MaxPlatformVersion 是8.0。 這表示, 參考管理員會篩選出 Windows 8.1 專案C++的 Microsoft Visual Runtime 封裝, 而當[!INCLUDE[win81](../debugger/includes/win81_md.md)]專案參考它時, MSBuild 會擲回錯誤。 注意: 從開始[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)], 支援此元素。

7. AppliesTo藉由指定適用的 Visual Studio 專案類型, 指定 [參考管理員] 中可用的 Sdk。 可辨識的九個值:WindowsAppContainer、VisualC、VB、CSharp、WindowsXAML、JavaScript、Managed 和 Native。 SDK 作者可以使用和 ("+ ') 或 ("&#124;"), 而不是 ("! ")運算子, 以確切指定套用至 SDK 的專案類型範圍。

    WindowsAppContainer 會識別應用[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]程式的專案。

8. SupportPrefer32Bit:支援的值為 "True" 和 "False"。 預設值為 "True"。 如果此值設定為 "False", 則如果參考 SDK 的專案[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]已啟用 Prefer32Bit, MSBuild 會傳回專案的錯誤 (或桌面專案的警告)。 如需 Prefer32Bit 的詳細資訊, 請參閱 [專案設計工具]、[[專案設計工具] (C#)](../ide/reference/build-page-project-designer-csharp.md)或[[編譯] 頁面 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)。

9. SupportedArchitectures:SDK 支援的架構清單 (以分號分隔)。 如果不支援使用中專案的目標 SDK 架構, MSBuild 會顯示警告。 如果未指定這個屬性, MSBuild 就不會顯示這種類型的警告。

10. SupportsMultipleVersions:如果此屬性設定為 [**錯誤**] 或 [**警告**], MSBuild 會指出相同的專案無法參考相同 SDK 系列的多個版本。 如果這個屬性不存在, 或設為 [**允許**], MSBuild 就不會顯示這種類型的錯誤或警告。

11. 約指定磁片上 Windows 元件庫之應用程式套件的路徑。 這個值會在本機的調試過程中傳遞至 Windows 元件程式庫的註冊元件。 檔案名的命名慣例是 *\<Company >。\<產品 >。\<架構 >。\<設定 >。版本\<> .appx*。 如果屬性名稱和屬性值不適用於 Windows 元件程式庫, 則設定和架構是選擇性的。 此值僅適用于 Windows 元件程式庫。

12. CopyRedistToSubDirectory:指定應該將 *\redist*資料夾下的檔案複製到相對於應用程式套件根目錄的位置 (也就是在 [**建立應用程式套件**] 中選擇的**套件位置**) 和執行時間配置根。 預設位置為應用程式套件的根目錄和**F5**版面配置。

13. DependsOn定義此 SDK 相依之 Sdk 的 SDK 身分識別清單。 這個屬性會出現在 [參考管理員] 的 [詳細資料] 窗格中。

14. MoreInfo:提供說明和詳細資訊的網頁 URL。 這個值會用於 [參考管理員] 右窗格中的 [詳細資訊] 連結。

15. 註冊類型:在應用程式資訊清單中指定 WinMD 註冊, 而原生 WinMD 需要有對應的執行 DLL。

16. 檔案參考:僅針對包含控制項或原生 Winmd 的參考指定。 如需如何指定參考是否包含控制項的詳細資訊, 請參閱下面的[指定工具箱專案的位置](#ToolboxItems)。

## <a name="ToolboxItems"></a>指定工具箱專案的位置

*Sdkmanifest.xml*架構的**ToolBoxItems**元素會指定工具箱專案在平臺和延伸模組 sdk 中的分類和位置。 下列範例示範如何指定不同的位置。 這適用于 WinMD 或 DLL 參考。

1. 將控制項放在 [工具箱] 預設分類中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 將控制項放在特定分類名稱之下。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. 將控制項放在特定類別目錄名稱之下。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. 在 Blend 和 Visual Studio 中, 將控制項放在不同的分類名稱之下。

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. 在 Blend 和 Visual Studio 中以不同方式列舉特定控制項。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 列舉特定控制項, 並將它們放在 [Visual Studio 一般路徑] 或 [全部控制項] 群組底下。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 列舉特定控制項, 並只在 ChooseItems 中顯示特定集合, 而不在工具箱中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>另請參閱

- [逐步解說：使用建立 SDKC++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [逐步解說：使用C#或 VISUAL BASIC 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [管理專案中的參考](../ide/managing-references-in-a-project.md)