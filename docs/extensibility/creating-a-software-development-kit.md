---
title: 建立軟體開發工具套件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739600"
---
# <a name="create-a-software-development-kit"></a>建立軟體開發工具組

軟體開發工具套件 (SDK) 是 API 的集合,您可以將其作為 Visual Studio 中的單個專案引用。 "**參考管理員**'對話框列出了與項目相關的所有 SDK。 將 SDK 添加到專案時,API 可在可視化工作室中使用。

有兩種類型的 SDK:

- 平臺 SDK 是開發平臺應用的必填元件。 例如,SDK[!INCLUDE[win81](../debugger/includes/win81_md.md)]是[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]開發 應用所必需的。

- 擴展 SDK 是擴充平臺的可選元件,但不是強制性的為該平台開發應用。

以下各節介紹 SDK 的一般基礎結構以及如何創建平臺 SDK 和擴展 SDK。

## <a name="platform-sdks"></a>平台 SDK

平臺 SDK 需要為平臺開發應用。 例如,SDK[!INCLUDE[win81](../debugger/includes/win81_md.md)]需要[!INCLUDE[win81](../debugger/includes/win81_md.md)]為開發應用。

### <a name="installation"></a>安裝

所有平台 SDK 都將安裝在*HKLM_\\軟體\微軟 SDK [TPI][tPV]\\ @InstallationFolder [ SDK 根]*。 因此,SDK[!INCLUDE[win81](../debugger/includes/win81_md.md)]安裝在*HKLM_軟體\微軟 SDK_Windows_v8.1*。

### <a name="layout"></a>配置

平台 SDK 具有以下佈局:

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

| 節點 | 描述 |
|------------------------| - |
| *參考*資料夾 | 包含可以編碼的 API 的二進位檔案。 這些可能包括 Windows 中數據 (WinMD) 檔案或程式集。 |
| *設計時間*資料夾 | 包含僅在運行/調試前需要的檔。 這些可能包括 XML 文件、庫、標頭、工具箱設計時間二進位檔案、MSBuild 專案等<br /><br /> 理想情況下,XML 文件將放置在 *_DesignTime*資料夾中,但引用的 XML 文件將繼續與 Visual Studio 中的參考檔一起放置。 例如,引用的XML文<em>檔\\[ 參考 ]config]\\[arch]_sample.dll</em>將為 *[參考\\]config]\\[arch_c_c.xml),* 該文檔的當地語系化版本將為 [*\\參考 ]config]\\\\[arch] [locale]_sample.xml*。 |
| *設定*資料夾 | 只能有三個資料夾:*除錯*,*零售*與*通用設定*。 如果應使用同一組 SDK 檔,SDK 作者可以將其檔置於 *「通用設定」* 下,而不管 SDK 消費者將針對哪個配置。 |
| *結構結構*資料夾 | 任何支援的*體系結構*資料夾都可以存在。 Visual Studio 支援以下體系結構:x86、x64、ARM 和中性。 注意:Win32 映射到 x86,AnyCPU 映射到中性。<br /><br /> MSBuild 僅在平臺 SDK 的 *[通用配置]中性*下查找。 |
| *SDKManifest.xml* | 此檔描述可視化工作室應如何使用 SDK。 檢視 SDK[!INCLUDE[win81](../debugger/includes/win81_md.md)]清單:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **顯示名稱:** 物件瀏覽器在「瀏覽」列表中顯示的值。<br /><br /> **平台識別:** 此屬性的存在告訴 Visual Studio 和 MSBuild SDK 是一個平臺 SDK,並且從它添加的引用不應在本地複製。<br /><br /> **目標框架:** Visual Studio 使用此屬性來確保只有針對此屬性值中指定的相同框架的專案才能使用 SDK。<br /><br /> **最小VSVersion:** Visual Studio 使用此屬性僅使用應用於它的 SDK。<br /><br /> **參考:** 必須僅為包含控制項的引用指定此屬性。 有關如何指定引用是否包含控制項的資訊,請參閱下文。 |

## <a name="extension-sdks"></a>延伸模組 SDK

以下各節介紹部署擴展 SDK 需要執行哪些操作。

### <a name="installation"></a>安裝

可以為特定使用者或所有使用者安裝擴展 SDK,而無需指定註冊表項。 要為所有使用者安裝 SDK,請使用以下路徑:

*%程式檔案 %\微軟\<SDK\>目標平臺\>\v<平台 版本號\擴展 Sdk*

對特定於使用者的安裝,請使用以下路徑:

*%USERPROFILE%*AppData_本地_微軟 SDK\<\>目標平臺\>\v<平台 版本號 \擴展 Sdk*

如果要使用其他位置,必須執行兩項操作之一:

1. 在註冊表項目中指定它:

     **HKLM_軟體\<_微軟SDK目標平臺>\v<平臺版本\>號 [擴展SDK\<名稱\<>SDKversion>**\

     並添加值為的`<path to SDK><SDKName><SDKVersion>`(預設)子鍵。

2. 將 MSBuild`SDKReferenceDirectoryRoot`屬性添加到專案檔中。 此屬性的值是要引用的擴展 SDK 駐留的目錄的分號分隔清單。

### <a name="installation-layout"></a>安裝佈局

延伸 SDK 以以下安裝佈局:

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

1. \\<\> \\ SDKName\><SDKVersion: 擴充 SDK 的名稱和版本派生自 SDK 根路徑中的相應資料夾名稱。 MSBuild 使用此識別在磁碟上尋找 SDK,Visual Studio 將在 **「屬性」** 視窗和**參考管理器**對話框中顯示此標識。

2. *引用*資料夾:包含 API 的二進位檔案。 這些可能是 Windows 中數據 (WinMD) 檔案或程式集。

3. *Redist*資料夾:運行時/調試所需的檔,應打包為使用者應用程式的一部分。 所有二進位檔應放置在*\\[redist\>\\\><配置<拱门*下, 二進位元名稱應具有以下格式,以確保唯一性: *]*\<公司>。\<產品>。\<目的>。\<延伸><em>。例如,[微軟.Cpp.Build.dll。</em> 所有名稱可能與其他 SDK 的檔名(例如 javascript、css、pri、xaml、png 和 jpg 檔)衝突的檔都應放置在<em>\\[redist<配置\>\\\>\\\>\*<arch<sdkname 下,但與 XAML 控件關聯的檔除外。這些檔應放置在 [redist<\\\>\\配置<\>\\拱\>形<组件名称</em>下。

4. *DesignTime*資料夾:僅在運行/調試前需要的檔,不應打包為使用者應用程式的一部分。 這些可以是 XML 文件、庫、標頭、工具箱設計時間二進位檔案、MSBuild 工件等。 任何供本機專案使用的 SDK 都必須具有*SDKName.props*檔。 下面顯示了這種類型的檔的範例。

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

    XML 引用文檔放在引用檔旁邊。 例如 *,_\\參考<配置\>\\\><arch _sample.dll*程式集的 XML 引用文檔是 *_\\參考<\>\\配置<\>arch _sample.xml,* 並且該文檔的當地語系化版本是*\\_reference<<\> \\<區域\>設置 _sample.xml\>\\*的配置。

5. *設定*資料夾:三個子資料夾:*除錯*,*零售*與*通用設定*。 當應使用同一組 SDK 檔時,SDK 作者可以將其檔置於 *「通用設定」* 下,而不管 SDK 消費者所針對的配置如何。

6. *體系結構*資料夾:支援以下體繫結構:x86、x64、ARM、中性。 Win32 對應到 x86,AnyCPU 映射到中性。

### <a name="sdkmanifestxml"></a>SDKManifest.xml

*SDKManifest.xml*檔案描述了 Visual Studio 應如何使用 SDK。 以下是一個範例：

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

下面的清單提供檔案的元素:

1. 顯示名稱:顯示在 Visual Studio 用戶介面中的參考管理器、解決方案資源管理器、物件瀏覽器和其他位置中的值。

2. 產品名稱:整體 SDK 產品名稱。 例如[!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)],SDK 被命名為"Microsoft.WinJS.1.0"和"Microsoft.WinJS.2.0",它們屬於同一個 SDK 產品系列「Microsoft.WinJS」。。 此屬性允許 Visual Studio 和 MSBuild 進行該連接。 如果此屬性不存在,SDK 名稱將用作產品系列名稱。

3. 框架標識:指定對一個或多個 Windows 元件庫的依賴項。 此屬性的值將放入使用應用的清單中。 此屬性僅適用於 Windows 元件庫。

4. 目標框架:指定參考管理員和工具箱中可用的 SDK。 這是目標框架名字的分號分隔清單,例如".NET框架,版本_v2.0;.NET 框架,版本_v4.5.1"。 如果指定了同一目標框架的多個版本,則參考管理器將使用最低指定版本進行篩選。 例如,如果指定了".NET框架、版本=v2.0;.NET 框架、版本=v4.5.1",則參考管理器將使用".NET 框架,版本=v2.0"。 如果指定了特定的目標框架配置檔,則參考管理器將僅使用該配置檔進行篩選。 例如,當指定「銀色光,版本=v4.0,配置檔=WindowsPhone」時,參考管理器僅篩選 Windows Phone 配置檔;面向完整 Silverlight 4.0 框架的專案在參考管理器中看不到 SDK。

5. 最小視頻工作室版本。

6. MaxPlatformVerson:最大目標平臺版本應用於指定擴展 SDK 無法正常工作的平臺版本。 例如,Microsoft Visual C++運行時包 v11.0 應僅由 Windows 8 專案引用。 因此,Windows 8 專案的 MaxPlatformVersion 是 8.0。 這意味著參考管理器篩選出適用於 Windows 8.1 專案的 Microsoft Visual C++運行時包,[!INCLUDE[win81](../debugger/includes/win81_md.md)]並且 MSBuild 在 專案引用時引發錯誤。 注意:此元素受支援,在[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]中啟動。

7. 應用到:透過指定適用的 Visual Studio 專案類型,指定參考管理器中可用的 SDK。 可以識別九個值:WindowsApp 容器、VisualC、VB、CSharp、WindowsXAML、JAvaScript、託管和本機。 SDK 作者可以使用 和 ("*"),或 ("&#124;"),而不是 ("!"運算符以精確指定應用於 SDK 的項目類型的範圍。

    WindowsApp 容器識別應用的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]專案 。

8. 支援首選32位:支援的值為"True"和"False"。 默認值為"True"。 如果該值設置為「False」,則如果引用 SDK 的[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]專案已 啟用了「首選32Bit」,則 MSBuild 將返回專案錯誤(或桌面專案警告)。 有關"首選32Bit"的詳細資訊,請參閱[生成頁、專案設計器 (C#)](../ide/reference/build-page-project-designer-csharp.md)或[編譯頁、專案設計器(可視化基本版)。](../ide/reference/compile-page-project-designer-visual-basic.md)

9. 支援的體系結構:SDK 支援的體系結構的分號分隔清單。 如果不需要使用項目中的目標 SDK 體系結構,則 MSBuild 將顯示一條警告。 如果未指定此屬性,MSBuild 永遠不會顯示這種類型的警告。

10. 支援多個版本:如果此屬性設置為**錯誤**或**警告**,MSBuild 指示同一專案不能引用同一 SDK 系列的多個版本。 如果此屬性不存在或設置為 **「允許**」,MSBuild 不會顯示這種類型的錯誤或警告。

11. AppX:指定磁碟上的 Windows 元件庫的應用包的路徑。 此值在本地調試期間傳遞到 Windows 元件庫的註冊元件。 檔名的命名約定是*\<公司>。\<產品>。\<體系結構>。\<配置>。版本\<>.appx*。 配置和體系結構在屬性名稱和屬性值中是可選的,如果它們不適用於 Windows 元件庫。 此值僅適用於 Windows 元件庫。

12. CopyRedisttoSubDirectory:指定在 *#redist*資料夾下的檔案應相對於應用套件根目錄(即 **"創建應用包"** 嚮導中選擇**的包位置**)和運行時佈局根目錄複製的位置。 默認位置是應用包和**F5**佈局的根。

13. DependsOn:定義此 SDK 所依賴的 SDK 的 SDK 標識清單。 此屬性將顯示在參考管理器的詳細資訊窗格中。

14. 更多資訊:提供説明和更多資訊的網頁 URL。 此值用於參考管理器右側窗格中的"詳細資訊"連結。

15. 註冊類型:在應用清單中指定 WinMD 註冊,並且本機 WinMD 需要註冊,該註冊具有對應實現 DLL。

16. 檔引用:僅為包含控制項或本機 WinMd 的引用指定。 有關如何指定參考是否包含控制項的資訊,請參考[在下面指定工具箱項目的位置](#ToolboxItems)。

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>指定工具箱項目的位置

*SDKManifest.xml*架構中的**ToolBoxItems**元素指定平台和擴展 SDK 中工具箱項的類別和位置。 以下範例示範如何指定不同位置。 這適用於 WinMD 或 DLL 參考。

1. 將控制項放在工具箱預設類別中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. 將控制項放在特定類別名稱下。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. 將控制項放在特定類別名稱下。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. 在混合和可視化工作室中將控件放在不同的類別名稱下。

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. 在混合和可視化工作室中以不同的方式枚舉特定控件。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. 枚舉特定控件,並將其置於可視化工作室通用路徑或僅在"所有控制"組中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. 枚舉特定控制項,並在「選擇專案」中僅顯示特定集,而不在工具箱中。

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>另請參閱

- [演練:使用C++創建 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [演練:使用 C# 或視覺化基本功能建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [管理專案中的參考](../ide/managing-references-in-a-project.md)
