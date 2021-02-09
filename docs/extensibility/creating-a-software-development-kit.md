---
title: 建立軟體發展工具組 |Microsoft Docs
description: 瞭解 Sdk 的一般基礎結構，以及如何建立平臺 SDK 和擴充功能 SDK。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74e31cb8fddb00e8a6771a6ad3065bce57cc8bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902245"
---
# <a name="create-a-software-development-kit"></a>建立軟體發展工具組

軟體發展工具組 (SDK) 是一組 Api，您可以在 Visual Studio 中參考為單一專案。 [ **參考管理員** ] 對話方塊會列出與專案相關的所有 sdk。 當您將 SDK 新增至專案時，Visual Studio 提供 Api。

Sdk 有兩種類型：

- 平臺 Sdk 是針對平臺開發應用程式的必要元件。 例如， [!INCLUDE[win81](../debugger/includes/win81_md.md)] 必須有 SDK 才能開發 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式。

- 延伸模組 Sdk 是擴充平臺的選用元件，但不是針對該平臺開發應用程式的必要元件。

下列各節說明 Sdk 的一般基礎結構，以及如何建立平臺 SDK 和擴充功能 SDK。

## <a name="platform-sdks"></a>平台 SDK

需要平臺 Sdk 才能開發平臺的應用程式。 例如， [!INCLUDE[win81](../debugger/includes/win81_md.md)] 需要 SDK 才能開發的應用程式 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 。

### <a name="installation"></a>安裝

所有平臺 Sdk 都會安裝在 *HKLM\Software\Microsoft\Microsoft sdk \\ [TPI] \V [TPV] \\ @InstallationFolder = [SDK root]*。 因此， [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK 會安裝在 *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*。

### <a name="layout"></a>Layout

平臺 Sdk 具有下列版面配置：

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

| 節點 | Description |
|------------------------| - |
| *參考* 資料夾 | 包含二進位檔，其中包含可針對進行編碼的 Api。 這些可能包含 Windows 中繼資料 (WinMD) 檔案或元件。 |
| *DesignTime* 資料夾 | 包含只有在執行前/調試時間才需要的檔案。 這些可能包括 XML 檔、文件庫、標頭、工具箱設計階段二進位檔、MSBuild 成品等等。<br /><br /> XML 檔最好是放在 *\DesignTime* 資料夾中，但是參考的 xml 檔會在 Visual Studio 的參考檔案中繼續放置在一起。 例如，參考 <em>\References \\ [config] \\ [架構] \sample.dll</em> 的 XML 檔將會是 *\References \\ [config] [架構 \\ ] \sample.xml*，而該檔的當地語系化版本將會是 *\References \\ [config] [架構 \\ ] \\ [locale] \sample.xml*。 |
| 設定資料夾 | 只能有三個資料夾： *Debug*、 *Retail* 和 *CommonConfiguration*。 SDK 作者可以將檔案放在 *CommonConfiguration* 下，如果應該取用相同的 sdk 檔案集，不論 sdk 取用者的目標是什麼設定都一樣。 |
| *架構* 資料夾 | 任何支援的 *架構* 資料夾都可以存在。 Visual Studio 支援下列架構： x86、x64、ARM 和中性。 注意： Win32 會對應至 x86，而 AnyCPU 則對應至中性。<br /><br /> MSBuild 只會在平臺 Sdk 的 *\CommonConfiguration\neutral* 下尋找。 |
| *SDKManifest.xml* | 此檔案描述 Visual Studio 應如何使用 SDK。 查看 SDK 資訊清單中的 [!INCLUDE[win81](../debugger/includes/win81_md.md)] ：<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName：** 物件瀏覽器在瀏覽清單中顯示的值。<br /><br /> **PlatformIdentity：** 這個屬性的存在會告訴 Visual Studio 和 MSBuild SDK 是 platform SDK，而從該 sdk 新增的參考不應在本機複製。<br /><br /> **TargetFramework：** Visual Studio 會使用這個屬性，以確保只有以這個屬性的值中指定的相同架構為目標的專案，才可以使用 SDK。<br /><br /> **MinVSVersion：** Visual Studio 使用這個屬性來只取用適用于它的 Sdk。<br /><br /> **參考：** 必須針對包含控制項的參考，指定這個屬性。 如需有關如何指定參考是否包含控制項的詳細資訊，請參閱下面的。 |

## <a name="extension-sdks"></a>擴充功能 SDK

下列各節說明部署擴充功能 SDK 所需執行的作業。

### <a name="installation"></a>安裝

您可以為特定使用者或所有使用者安裝擴充功能 Sdk，而不需要指定登錄機碼。 若要為所有使用者安裝 SDK，請使用下列路徑：

*% Program Files%\Microsoft Sdk \<target platform\> \v<platform version number \> \ExtensionSDKs*

若為使用者特定安裝，請使用下列路徑：

*%USERPROFILE%\AppData\Local\Microsoft Sdk \<target platform\> \v<platform 版本號碼 \> \ExtensionSDKs*

如果您想要使用不同的位置，您必須執行下列其中一項動作：

1. 在登錄機碼中指定它：

     **HKLM\Software\Microsoft\Microsoft Sdk \<target platform> \v<platform 版本號碼 \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     並新增 (預設) 子機碼，其值為 `<path to SDK><SDKName><SDKVersion>` 。

2. 將 MSBuild 屬性加入 `SDKReferenceDirectoryRoot` 至您的專案檔。 這個屬性的值是以分號分隔的目錄清單，其中包含您想要參考的擴充功能 Sdk。

### <a name="installation-layout"></a>安裝版面配置

擴充功能 Sdk 具有下列安裝版面配置：

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

1. \\<SDKName \> \\<SDKVersion \> ：擴充功能 SDK 的名稱和版本衍生自 sdk 根目錄路徑中對應的資料夾名稱。 MSBuild 會使用此身分識別來尋找磁片上的 SDK，Visual Studio 在 [ **屬性** ] 視窗和 [ **參考管理員** ] 對話方塊中顯示此身分識別。

2. *參考* 資料夾：包含 api 的二進位檔。 這些可能是 (WinMD) 檔或元件的 Windows 中繼資料。

3. 可轉散發 *套件資料夾：* 執行時間/偵錯工具所需的檔案，應封裝為使用者應用程式的一部分。 所有二進位檔都應該放在 *\redist \\<config \> \\<\>* 架構下，而且二進位名稱應該具有下列格式，以確保唯一性： *]* \<company> ... \<product> \<purpose> \<extension><em>.例如，* Microsoft.Cpp.Build.dll</em>。 名稱與其他 Sdk 的檔案名可能相衝突的所有檔案 (例如，javascript、css、pri、xaml、png 和 jpg 檔案) 應放置在<em>\redist \\<config \> \\<架構<sdkname 之下， \> \\ \> \* 但與 xaml 控制項相關聯的檔案除外。這些檔案應該放在 * \redist \\<config \> \\<架構 \> \\<componentname \> \\ 之下</em>。

4. *DesignTime* 資料夾：只在執行前/調試時間所需的檔案，不應封裝為使用者應用程式的一部分。 這些可以是 XML 檔、文件庫、標頭、工具箱設計階段二進位檔、MSBuild 成品等等。 原生專案所使用的任何 SDK 都必須有 *SDKName .props* 檔案。 以下顯示這種檔案類型的範例。

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

    XML 參考檔會放在參考檔案的旁邊。 例如， *\References \\<config \> \\<架構 \>\sample.dll* 元件的 XML 參考檔是 *\References \\<config \> \\<架構 \>\sample.xml*，而該檔的當地語系化版本 \References<設定<架構 *<\\ 地區設定 \> \\ \> \\ \>\sample.xml*。

5. 設定 *資料夾：三個子資料夾：* *Debug*、 *Retail* 和 *CommonConfiguration*。 無論 SDK 取用者的目標設定為何，SDK 作者都可以使用相同的 SDK 檔案集合，將檔案放在 *CommonConfiguration* 下。

6. *架構* 資料夾：支援下列架構： x86、X64、ARM、中性。 Win32 對應至 x86，且 AnyCPU 對應至中性。

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*SDKManifest.xml* 檔案描述 Visual Studio 應該如何使用 SDK。 以下是一個範例：

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

下列清單提供檔案的元素：

1. DisplayName：出現在 [參考管理員]、[方案總管]、[物件瀏覽器] 中的值，以及用於 Visual Studio 的使用者介面中的其他位置。

2. ProductFamilyName：整體 SDK 產品名稱。 例如，sdk 的 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] 名稱為 "WinJS" 和 "WinJS"，其屬於相同的 SDK 產品系列，也就是 "WinJS"。 這個屬性可讓 Visual Studio 和 MSBuild 進行該連接。 如果這個屬性不存在，則會使用 SDK 名稱作為產品系列名稱。

3. FrameworkIdentity：指定一或多個 Windows 元件程式庫的相依性。 這個屬性的值會放入取用應用程式的資訊清單中。 這個屬性只適用于 Windows 元件程式庫。

4. TargetFramework：指定可在 [參考管理員] 和 [工具箱] 中使用的 Sdk。 這是以分號分隔的目標 framework 名字標記清單，例如 ".NET Framework，version = v2.0; .NET Framework，version = v1.0"。 如果指定了數個相同的目標 framework 版本，則參考管理員會使用最低的指定版本進行篩選。 例如，如果指定了 ".NET Framework，version = v2.0; .NET Framework，version = v1.0"，則參考管理員會使用 ".NET Framework，version = v2.0"。 如果指定了特定的目標 framework 設定檔，則參考管理員只會使用該設定檔進行篩選。 例如，當指定 "Silverlight，version = v4.0，profile = WindowsPhone" 時，參考管理員只會篩選 Windows Phone 設定檔;以完整 Silverlight 4.0 架構為目標的專案不會在參考管理員中看到 SDK。

5. MinVSVersion：最低 Visual Studio 版本。

6. MaxPlatformVerson：最大目標平臺版本應該用來指定您的延伸模組 SDK 將無法運作的平臺版本。 例如，Microsoft Visual C++ 執行時間套件 v 11.0 只能由 Windows 8 專案參考。 因此，Windows 8 專案的 MaxPlatformVersion 是8.0。 這表示，參考管理員會篩選出 Windows 8.1 專案的 Microsoft Visual C++ 執行時間封裝，而當專案參考時，MSBuild 會擲回錯誤 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 。 注意：從開始，支援這個元素 [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] 。

7. AppliesTo：指定適用的 Visual Studio 專案類型，以指定參考管理員中的可用 Sdk。 可辨識九個值： WindowsAppContainer、VisualC、VB、CSharp、WindowsXAML、JavaScript、Managed 和 Native。 SDK 作者可以使用及 ( "+ ' ) ，或 (" &#124; ") ，而不是 ("！ ") 運算子，以明確指定適用于 SDK 的專案類型範圍。

    WindowsAppContainer 識別 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的專案。

8. SupportPrefer32Bit：支援的值為 "True" 和 "False"。 預設值為 "True"。 如果值設定為 "False"，MSBuild 會傳回專案的錯誤 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] (或桌面專案的警告) 如果參考 SDK 的專案已啟用 Prefer32Bit。 如需有關 Prefer32Bit 的詳細資訊，請參閱 [專案設計工具] [ (c # ) ](../ide/reference/build-page-project-designer-csharp.md) 或 [ [編譯] 頁面的 [專案設計工具] (Visual Basic) ](../ide/reference/compile-page-project-designer-visual-basic.md)。

9. SupportedArchitectures： SDK 所支援的架構清單（以分號分隔）。 如果不支援取用專案中的目標 SDK 架構，MSBuild 會顯示警告。 如果未指定此屬性，MSBuild 永遠不會顯示這種類型的警告。

10. SupportsMultipleVersions：如果這個屬性設為 [ **錯誤** ] 或 [ **警告**]，MSBuild 會指出相同的專案無法參考相同 SDK 系列的多個版本。 如果這個屬性不存在，或設為 [ **允許**]，MSBuild 不會顯示這個類型的錯誤或警告。

11. AppX：指定磁片上 Windows 元件庫之應用程式套件的路徑。 此值會在本機偵錯工具期間傳遞至 Windows 元件庫的註冊元件。 檔案名的命名 *慣例為 ...。 \<Company> \<Product> \<Architecture> \<Configuration> \<Version>appx*。 如果屬性名稱和屬性值未套用至 Windows 元件庫，則設定和架構是選擇性的。 此值僅適用于 Windows 元件程式庫。

12. CopyRedistToSubDirectory：指定要將 *\redist* 資料夾下的檔案複製到應用程式套件根目錄的位置， (也就是在 [**建立應用程式套件**] 中選擇的 **套件位置**) 和執行時間配置根。 預設位置為應用程式套件的根目錄和 **F5** 版面配置。

13. DependsOn：定義此 SDK 所依存之 sdk 的 SDK 身分識別清單。 這個屬性會出現在 [參考管理員] 的 [詳細資料] 窗格中。

14. MoreInfo：提供說明和詳細資訊之網頁的 URL。 此值可用於參考管理員右窗格中的 [詳細資訊] 連結。

15. 註冊類型：指定應用程式資訊清單中的 WinMD 註冊，而且原生 WinMD 需要有對應的執行 DLL。

16. 檔案參考：僅針對包含控制項或原生 Winmd 的參考指定。 如需有關如何指定參考是否包含控制項的詳細資訊，請參閱 [在下方指定工具箱專案的位置](#ToolboxItems) 。

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> 指定工具箱專案的位置

*SDKManifest.xml* 架構的 **ToolBoxItems** 元素會指定 [工具箱] 專案在平臺和延伸模組 sdk 中的分類和位置。 下列範例顯示如何指定不同的位置。 這適用于 WinMD 或 DLL 參考。

1. 將控制項放在 [工具箱] 預設分類中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 將控制項放在特定的類別目錄名稱之下。

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

4. 將控制項放在 Blend 和 Visual Studio 中的不同類別目錄名稱之下。

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. 在 Blend 和 Visual Studio 中以不同方式列舉特定的控制項。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 列舉特定的控制項，並將它們放在 Visual Studio 通用路徑或只放在 [所有控制項] 群組中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 列舉特定的控制項，並只在 ChooseItems 中顯示特定的集合，而不是在 [工具箱] 中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>另請參閱

- [逐步解說：使用 c + + 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [逐步解說：使用 c # 或 Visual Basic 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [管理專案中的參考](../ide/managing-references-in-a-project.md)
