---
title: VSIX 擴展架構 2.0 參考 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697920"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 延伸架構 2.0 引用
VSIX 部署清單檔描述 VSIX 包的內容。 檔案格式由架構控制。 此架構的版本2.0支援添加自定義類型和屬性。  清單的架構是可擴展的。 清單載入程式忽略它不理解的XML元素和屬性。

> [!IMPORTANT]
> Visual Studio 2015 可在 Visual Studio 2010、Visual Studio 2012 或 Visual Studio 2013 格式中載入 VSIX 檔。

## <a name="package-manifest-schema"></a>套件清單架構
 清單XML檔案的根元素是`<PackageManifest>`。 它有一個屬性`Version`,這是清單格式的版本。 如果對格式進行了重大更改,則版本格式將更改。 本文介紹清單格式版本 2.0,該版本通過在清單中指定,`Version`將 屬性設置為版本="2.0"的值。

### <a name="packagemanifest-element"></a>套件清單項目
 在根`<PackageManifest>`元素中,可以使用以下元素:

- `<Metadata>`- 有關包本身的元數據和廣告資訊。 清單中`Metadata`只允許一個元素。

- `<Installation>`- 本節定義安裝此擴展包的方式,包括它可以安裝到的應用程式 SKU。 清單中只允許`Installation`單個元素。 清單必須具有`Installation`元素,否則此包不會安裝到任何 SKU 中。

- `<Dependencies>`- 此處定義了此包的可選依賴項清單。

- `<Assets>`- 本節包含此包中包含的所有資產。 如果沒有此部分,此包將不會顯示任何內容。

- `<AnyElement>*`- 清單架構足夠靈活,可以允許任何其他元素。 清單載入程式無法識別的任何子元素在擴充管理器 API 中作為額外的 XmlElement 物件公開。 使用這些子元素,VSIX 擴展可以在清單檔中定義 Visual Studio 中運行的代碼在運行時可以訪問的其他數據。 請參考[Microsoft. VisualStudio.擴充管理員.I擴展.附加元素](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120))。

### <a name="metadata-element"></a>中繼資料元素
 本節是關於包、其標識和廣告資訊的元數據。 `<Metadata>`包含以下元素:

- `<Identity>`- 定義此套件的識別資訊,並包括以下屬性:

  - `Id`- 此屬性必須是其作者選擇的包的唯一 ID。 名稱應與 CLR 類型的名稱速度相同:Company.Product.Feature.Name。 該`Id`屬性限制為 100 個字元。

  - `Version`- 定義此包的版本及其內容。 此屬性遵循 CLR 程式集版本版本格式:主要.Minor.Build.修訂版 (1.2.40308.00)。 具有較高版本號的包被視為對包的更新,可以安裝在現有已安裝的版本上。

  - `Language`- 此屬性是包的預設語言,對應於此清單中的文本數據。 此屬性遵循資源程式集的 CLR 區域設定代碼約定,例如:en-us、en、fr-fr。 您可以指定`neutral`聲明將在 Visual Studio 的任何版本上運行的語言中立擴展。 預設值是 `neutral`。

  - `Publisher`- 此屬性標識此包的發行者,無論是公司還是個人名稱。 該`Publisher`屬性限制為 100 個字元。

- `<DisplayName>`- 此元素指定在擴展管理員 UI 中顯示的使用者友好套件名稱。 內容`DisplayName`限制為 50 個字元。

- `<Description>`- 此可選元素是擴展管理員 UI 中顯示的包及其內容的簡短說明。 內容`Description`可以包含所需的任何文本,但僅限於 1000 個字元。

- `<MoreInfo>`- 此可選元素是連線頁面的 URL,其中包含此包的完整說明。 協議必須指定為 HTTP。

- `<License>`- 此選擇元素是套件中包含的許可證檔 (.txt, .rtf) 的相對路徑。

- `<ReleaseNotes>`- 此可選元素是包中包含的發行說明檔(.txt,.rtf)的相對路徑,或者是顯示發行說明的網站的 URL。

- `<Icon>`- 此可選元素是包中包含的圖像檔(png、bmp、jpeg、ico)的相對路徑。 圖示影像應為 32x32 像素(或將縮小到該大小),並顯示在列表視圖 UI 中。 如果未`Icon`指定任何元素,UI 將使用預設值。

- `<PreviewImage>`- 此可選元素是包中包含的圖像檔(png、bmp、jpeg)的相對路徑。 預覽影像應為 200x200 像素,並顯示在詳細資訊 UI 中。 如果未`PreviewImage`指定任何元素,UI 將使用預設值。

- `<Tags>`- 此選擇元素列出了用於搜尋提示的其他分號分隔文字標記。 元素`Tags`限制為 100 個字元。

- `<GettingStartedGuide>`- 此選擇元素是指向 HTML 檔的相對路徑,或指向包含有關如何使用此套件中的延伸名或內容的資訊的網站的 URL。 本指南作為安裝的一部分啟動。

- `<AnyElement>*`- 清單架構足夠靈活,可以允許任何其他元素。 清單載入程式無法識別的任何子元素都公開為 XmlElement 物件的清單。 使用這些子元素,VSIX 擴展可以在清單檔中定義其他數據,並在運行時枚舉它們。

### <a name="installation-element"></a>安裝項目
 本節定義安裝此包的方式以及它可以安裝到的應用程式 SKU。 本節包含以下屬性:

- `Experimental`- 如果當前為所有使用者安裝了擴展,但正在同一台計算機上開發更新版本,則將此屬性設置為 true。 例如,如果您已為所有使用者安裝了 My 擴展 1.0,但希望在同一台電腦上調試 My 擴展 2.0,請設置"實驗","true"。 此屬性在 Visual Studio 2015 更新 1 及更高版本中可用。

- `Scope`- 此屬性可以採用值「全域」或「產品擴展」:

  - "全域"指定安裝範圍不限定為特定的 SKU。 例如,在安裝擴展 SDK 時使用此值。

  - "產品延伸"指定安裝擴展到單個 Visual Studio SKU 的傳統 VSIX 擴展(版本 1.0)。 這是預設值。

- `AllUsers`- 此選擇屬性指定是否將為此包安裝給所有使用者。 預設情況下,此屬性為 false,它指定包是每個使用者。 (將此值設定為 true 時,安裝使用者必須提升到管理許可權級別才能安裝生成的 VSIX。

- `InstalledByMsi`- 此選擇屬性指定此包是否由 MSI 安裝。 MSI 安裝的程式包由 MSI(程式和功能)安裝和管理,而不是由可視化工作室擴展管理器安裝和管理。  預設情況下,此屬性為 false,指定 MSI 未安裝套件。

- `SystemComponent`- 此選擇屬性指定是否應將此套件視為系統元件。 系統元件不顯示在擴展管理員 UI 中,並且無法更新。 預設情況下,此屬性為 false,指定套件不是系統元件。

- `AnyAttribute*`-`Installation`元素接受一組不限成員名額的屬性,這些屬性將在運行時作為名稱值對字典公開。

- `<InstallationTarget>`-此元素控制 VSIX 安裝程式安裝套件的位置。 如果`Scope`屬性的值是"Product 擴展",則包必須以 SKU 為目標,SKU 已安裝清單檔作為其內容的一部分,以通告其可用性到擴展。 當`<InstallationTarget>`屬性具有顯式或預設值「`Scope`產品 延伸」時,元素具有以下屬性:

  - `Id`- 此屬性標識包。  該屬性遵循命名空間約定:Company.Product.Feature.Name。 該`Id`屬性只能包含字母數位字元,並且限制為 100 個字元。 預期值:

    - 微軟.VisualStudio.集成外殼

    - Microsoft.VisualStudio.Pro

    - 微軟.VisualStudio.高級

    - 微軟.VisualStudio.終極

    - 微軟.VisualStudio.VWDExpress

    - 微軟.VisualStudio.VPDExpress

    - 微軟.VisualStudio.VSWinExpress

    - 微軟.VisualStudio.VSLS

    - 我的.Shell.應用程式

  - `Version`- 此屬性指定具有此 SKU 的最小和最大受支援版本的版本範圍。 包可以詳細說明它支援的 SKU 版本。 版本範圍表示法為 [10.0 - 11.0],其中

    - [ - 最小版本包括。

    - * - 最大版本(包括)。

    - (- 最小版本獨佔。

    - ) - 最大版本獨佔。

    - 單個版本 = - 僅指定版本。

    > [!IMPORTANT]
    > VSIX 架構的版本 2.0 在 Visual Studio 2012 中引入。 要使用此架構,您必須在電腦上安裝 Visual Studio 2012 或更高版本,並使用該產品的 VSIXInstaller.exe。 您可以使用 Visual Studio 2012 或更高版本的 VSIX 安裝程式定位早期版本的 Visual Studio,但只能透過使用安裝程式的更高版本。

    Visual Studio 2017 版本號可在[Visual Studio 版本號和發佈日期](../install/visual-studio-build-numbers-and-release-dates.md)中找到。

    當表示 Visual Studio 2017 版本的版本時,次要版本應始終為**0**。 例如,Visual Studio 2017 版本 15.3.26730.0 應表示為 [15.0.26730.0,16.0)。 這僅適用於 Visual Studio 2017 和更高版本號。

  - `AnyAttribute*`-`<InstallationTarget>`該元素允許一組開放式屬性,這些屬性在運行時作為名稱值對字典公開。

### <a name="dependencies-element"></a>相依項目
 此元素包含此包聲明的依賴項清單。 如果指定了任何依賴項,則這些包(由其`Id`標識)必須以前已安裝。

- `<Dependency>`元素 - 此子元素具有以下屬性:

  - `Id`- 此屬性必須是從屬包的唯一 ID。 此標識值必須與此`<Metadata><Identity>Id`包所依賴的包的屬性匹配。 該`Id`屬性遵循命名空間約定:Company.Product.Feature.Name。 該屬性只能包含字母數位字元,並且限制為 100 個字元。

  - `Version`- 此屬性指定具有此 SKU 的最小和最大受支援版本的版本範圍。 包可以詳細說明它支援的 SKU 版本。 版本範圍表示法為 [12.0, 13.0],其中:

    - [ - 最小版本包括。

    - * - 最大版本(包括)。

    - (- 最小版本獨佔。

    - ) - 最大版本獨佔。

    - 單個版本 = - 僅指定版本。

  - `DisplayName`- 此屬性是從屬包的顯示名稱,用於 UI 元素(如對話框和錯誤消息)。 除非 MSI 安裝從屬包,否則該屬性是可選的。

  - `Location`- 此選擇屬性指定此 VSIX 中相對路徑到嵌套 VSIX 套件或依賴項的下載位置的 URL。 此屬性用於幫助使用者找到先決條件包。

  - `AnyAttribute*`-`Dependency`元素接受一組不限成員名額的屬性,這些屬性將在運行時作為名稱值對字典公開。

### <a name="assets-element"></a>資產項目
 此元素包含此包顯示的每個`<Asset>`擴展或內容元素的標記清單。

- `<Asset>`- 這個元素包含以下屬性與元素:

  - `Type`- 此元素表示的擴展或內容的類型。 每個`<Asset>`元素必須具有單`Type`個 ,`<Asset>`但多個 元素可能`Type`具有相同的 。 根據命名空間約定,此屬性應表示為完全限定的名稱。 已知類型包括:

    1. 微軟.VisualStudio.Vs包

    2. Microsoft.VisualStudio.MefComponent

    3. 微軟.VisualStudio.工具箱控制

    4. 微軟.VisualStudio.範例

    5. 微軟.VisualStudio.專案範本

    6. 微軟.VisualStudio.專案範本

    7. 微軟.VisualStudio.組裝

       您可以創建自己的類型,並為他們提供唯一的名稱。 在 Visual Studio 內部運行時,程式碼可以通過擴展管理器 API 枚舉和訪問這些自定義類型。

  - `Path`- 包含資產的包中檔或資料夾的相對路徑。

  - `TargetVersion`- 給定資產適用的版本範圍。 用於將多個版本的資產運送到 Visual Studio 的不同版本。 需要 Visual Studio 2017.3 或更高版本才能生效。

  - `AnyAttribute*`- 一組開放式屬性,在運行時作為名稱值對字典公開。

    `<AnyElement>*`-`<Asset>`在 開始標記和結束標記之間允許任何結構化內容。 所有元素都公開為 XmlElement 物件的清單。 VSIX 擴展可以在清單檔中定義結構化特定於類型的元數據,並在運行時枚舉它們。

### <a name="sample-manifest"></a>範例清單

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>另請參閱

- [船舶視覺工作室擴展](../extensibility/shipping-visual-studio-extensions.md)
