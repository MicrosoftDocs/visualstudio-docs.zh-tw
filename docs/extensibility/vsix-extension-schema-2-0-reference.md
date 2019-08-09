---
title: VSIX 延伸模組架構2.0 參考 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9333f2fb1bff0fdb8a3f0dac8004f66156b8863d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870828"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 延伸模組架構2.0 參考
VSIX 部署資訊清單檔案描述 VSIX 封裝的內容。 檔案格式是由架構所控制。 此架構的2.0 版支援加入自訂類型和屬性。  資訊清單的架構是可擴充的。 資訊清單載入器會忽略不了解的 XML 元素和屬性。

> [!IMPORTANT]
> Visual Studio 2015 可以載入 Visual Studio 2010、Visual Studio 2012 或 Visual Studio 2013 格式的 VSIX 檔案。

## <a name="package-manifest-schema"></a>封裝資訊清單架構
 資訊清單 XML 檔案的根項目為`<PackageManifest>`。 它具有單一屬性`Version`, 也就是資訊清單格式的版本。 如果對格式進行重大變更, 則會變更版本格式。 本文說明資訊清單格式2.0 版, 其指定于資訊清單中, 方法是`Version`將屬性設定為 version = "2.0" 的值。

### <a name="packagemanifest-element"></a>PackageManifest 元素
 `<PackageManifest>`在根項目內, 您可以使用下列元素:

- `<Metadata>`-封裝本身的中繼資料和廣告資訊。 資訊清單`Metadata`中只允許一個元素。

- `<Installation>`-本節定義可安裝此延伸模組套件的方式, 包括可安裝到其中的應用程式 Sku。 資訊清單中`Installation`只允許單一元素。 資訊清單必須有`Installation`元素, 否則此封裝將不會安裝到任何 SKU 中。

- `<Dependencies>`-此套件的選擇性相依性清單定義于這裡。

- `<Assets>`-此區段包含此套件中包含的所有資產。 若沒有此區段, 此套件就不會呈現任何內容。

- `<AnyElement>*`-資訊清單架構具有足夠的彈性, 可允許任何其他元素。 資訊清單載入器無法辨識的任何子專案都會在擴充管理員 API 中公開為額外的 XmlElement 物件。 VSIX 擴充功能會使用這些子專案, 在資訊清單檔案中定義其他資料, 而這些程式碼會在執行時間中執行 Visual Studio 可以存取。 請參閱[VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120))。

### <a name="metadata-element"></a>Metadata 元素
 本節是關於封裝、其身分識別和廣告資訊的中繼資料。 `<Metadata>`包含下列元素:

- `<Identity>`-定義此封裝的識別資訊, 並包含下列屬性:

  - `Id`-此屬性必須是其作者所選擇之封裝的唯一識別碼。 名稱應該與 CLR 類型命名空間的方式相同:Company.Product.Feature.Name。 `Id`屬性限制為100個字元。

  - `Version`-定義此封裝及其內容的版本。 這個屬性會遵循 CLR 元件版本設定格式:主要. 次要. 組建修訂 (1.2.40308.00)。 版本號碼較高的套件會被視為套件的更新, 而且可以安裝在現有的已安裝版本上。

  - `Language`-這個屬性是封裝的預設語言, 而且會對應到此資訊清單中的文字資料。 這個屬性會遵循資源元件的 CLR 地區設定程式碼慣例, 例如: en-us、en、fr-fr。 您可以指定`neutral` , 以宣告將在任何版本的 Visual Studio 上執行的非語言相關延伸模組。 預設值為 `neutral`。

  - `Publisher`-這個屬性會識別此封裝的發行者, 也就是公司或個人名稱。 `Publisher`屬性限制為100個字元。

- `<DisplayName>`-這個元素會指定在擴充管理員 UI 中顯示的使用者易記套件名稱。 `DisplayName`內容限制為50個字元。

- `<Description>`-這個選擇性元素是封裝及其內容的簡短描述, 其顯示在擴充管理員 UI 中。 `Description`內容可以包含您想要的任何文字, 但長度限制為1000個字元。

- `<MoreInfo>`-此選擇性專案是線上網頁的 URL, 其中包含此封裝的完整描述。 通訊協定必須指定為 HTTP。

- `<License>`-此選擇性專案是封裝中所含授權檔案 (.txt、.rtf) 的相對路徑。

- `<ReleaseNotes>`-此選擇性專案是封裝 (.txt, .rtf) 中所包含之版本資訊檔案的相對路徑, 或者是顯示版本資訊之網站的 URL。

- `<Icon>`-這個選擇性元素是封裝中所包含影像檔案 (png、bmp、jpeg、.ico) 的相對路徑。 圖示影像應為32x32 圖元 (或將會壓縮成該大小), 並出現在 listview UI 中。 如果未`Icon`指定任何元素, 則 UI 會使用預設值。

- `<PreviewImage>`-此選擇性專案是封裝中所包含影像檔案 (png、bmp、jpeg) 的相對路徑。 預覽影像應為200x200 圖元, 並顯示在詳細資料 UI 中。 如果未`PreviewImage`指定任何元素, 則 UI 會使用預設值。

- `<Tags>`-此選擇性元素會列出用於搜尋提示的其他以分號分隔的文字標記。 `Tags`元素限制為100個字元。

- `<GettingStartedGuide>`-這個選擇性元素是 HTML 檔案的相對路徑或網站的 URL, 其中包含如何在此封裝內使用延伸模組或內容的相關資訊。 本指南會在安裝過程中啟動。

- `<AnyElement>*`-資訊清單架構具有足夠的彈性, 可允許任何其他元素。 資訊清單載入器無法辨識的任何子專案都是以 XmlElement 物件清單的形式公開。 使用這些子專案, VSIX 擴充功能可以在資訊清單檔中定義其他資料, 並在執行時間進行列舉。

### <a name="installation-element"></a>安裝元素
 本節定義此套件的安裝方式, 以及可安裝的應用程式 Sku。 此章節包含下列屬性:

- `Experimental`-如果您有目前已針對所有使用者安裝的延伸模組, 但您正在同一部電腦上開發更新的版本, 請將此屬性設定為 [true]。 例如, 如果您已為所有使用者安裝 MyExtension 1.0, 但想要在同一部電腦上進行 MyExtension 2.0 的偵錯工具, 請設定實驗 = "true"。 此屬性可在 Visual Studio 2015 Update 1 及更新版本中使用。

- `Scope`-此屬性可以採用 "Global" 或 "ProductExtension" 值:

  - 「全域」指定安裝不是特定 SKU 的範圍。 例如, 安裝延伸模組 SDK 時, 會使用此值。

  - "ProductExtension" 指定已安裝個別 Visual Studio Sku 的傳統 VSIX 延伸模組 (版本 1.0)。 這是預設值。

- `AllUsers`-此選擇性屬性會指定是否要針對所有使用者安裝此封裝。 根據預設, 此屬性為 false, 指定封裝為每位使用者。 (當您將此值設定為 true 時, 安裝的使用者必須提升為系統管理許可權等級, 才能安裝產生的 VSIX。

- `InstalledByMsi`-此選擇性屬性會指定 MSI 是否安裝此封裝。 Msi 安裝的套件是由 MSI ([程式和功能]) 所安裝及管理, 而不是由 Visual Studio 的擴充管理員進行安裝。  根據預設, 此屬性為 false, 指定 MSI 不會安裝封裝。

- `SystemComponent`-此選擇性屬性會指定是否應將此封裝視為系統元件。 系統元件不會顯示在擴充管理員 UI 中, 因此無法更新。 根據預設, 此屬性為 false, 指定封裝不是系統元件。

- `AnyAttribute*``Installation` -元素會接受一組開放式的屬性, 在執行時間會以名稱/值配對字典的形式公開。

- `<InstallationTarget>`-這個元素會控制 VSIX 安裝程式安裝封裝的位置。 如果`Scope`屬性的值為 "ProductExtension", 則封裝必須以 SKU 為目標, 而該 SKU 已安裝資訊清單檔案作為其內容的一部分, 以通告其對擴充功能的可用性。 當屬性具有明確或預設值 "ProductExtension" 時, `<InstallationTarget>`元素具有下列屬性: `Scope`

  - `Id`-這個屬性會識別封裝。  屬性會遵循命名空間慣例:Company.Product.Feature.Name。 `Id`屬性只能包含英數位元, 且長度限制為100個字元。 預期的值:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`-此屬性會指定版本範圍, 其中包含此 SKU 的最小和最大支援版本。 封裝可以詳細說明其支援的 Sku 版本。 版本範圍標記法為 [10.0-11.0], 其中

    - [-最低版本 (含)。

    - ]-最大版本 (含)。

    - (-最低版本專屬。

    - )-最大版本專有。

    - 單一版本 #-僅限指定的版本。

    > [!IMPORTANT]
    > Visual Studio 2012 中引進了版本2.0 的 VSIX 架構。 若要使用此架構, 您必須在電腦上安裝 Visual Studio 2012 或更新版本, 並使用屬於該產品的 VSIXInstaller。 您可以使用 Visual Studio 2012 或更新版本的 VSIXInstaller 來設定舊版的 Visual Studio, 但只能使用較新版本的安裝程式。

    Visual Studio 2017 版本號碼可在[Visual Studio 組建編號和發行日期](../install/visual-studio-build-numbers-and-release-dates.md)找到。

    表示 Visual Studio 2017 版本的版本時, 次要版本應一律為**0**。 例如, Visual Studio 2017 版本15.3.26730.0 應該表示為 [15.0.26730.0, 16.0)。 只有 Visual Studio 2017 和更新版本號碼才需要此值。

  - `AnyAttribute*``<InstallationTarget>` -元素允許一組開放式屬性, 在執行時間公開為名稱/值配對字典。

### <a name="dependencies-element"></a>相依性元素
 此元素包含此封裝所宣告的相依性清單。 如果指定了任何相依性, 則必須先安裝那些`Id`封裝 (由其所識別)。

- `<Dependency>`元素-這個子項目具有下列屬性:

  - `Id`-此屬性必須是相依封裝的唯一識別碼。 此識別值必須符合此`<Metadata><Identity>Id`封裝相依之封裝的屬性。 `Id`屬性會遵循命名空間慣例:Company.Product.Feature.Name。 屬性只能包含英數位元, 且長度限制為100個字元。

  - `Version`-此屬性會指定版本範圍, 其中包含此 SKU 的最小和最大支援版本。 封裝可以詳細說明其支援的 Sku 版本。 版本範圍標記法為 [12.0, 13.0], 其中:

    - [-最低版本 (含)。

    - ]-最大版本 (含)。

    - (-最低版本專屬。

    - )-最大版本專有。

    - 單一版本 #-僅限指定的版本。

  - `DisplayName`-這個屬性是相依套件的顯示名稱, 用於 UI 元素, 例如對話方塊和錯誤訊息。 除非 MSI 已安裝相依套件, 否則此屬性是選擇性的。

  - `Location`-此選擇性屬性會指定此 VSIX 中的相對路徑至嵌套的 VSIX 封裝, 或相依性下載位置的 URL。 此屬性是用來協助使用者尋找必要條件套件。

  - `AnyAttribute*``Dependency` -元素會接受一組開放式的屬性, 在執行時間會以名稱/值配對字典的形式公開。

### <a name="assets-element"></a>資產元素
 此元素包含此封裝所`<Asset>`呈現之每個延伸模組或內容元素的標記清單。

- `<Asset>`-此元素包含下列屬性和元素:

  - `Type`-此元素所表示的延伸模組或內容類型。 每`<Asset>`個元素都必須有`Type`單一的, `<Asset>`但多個元素可能`Type`會有相同的。 根據命名空間慣例, 此屬性應該表示為完整名稱。 已知的類型為:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       您可以建立自己的類型, 並為其指定唯一的名稱。 在 Visual Studio 內的執行時間, 您的程式碼可以透過擴充管理員 API 來列舉和存取這些自訂類型。

  - `Path`-封裝內包含資產之檔案或資料夾的相對路徑。

  - `TargetVersion`-套用指定資產的版本範圍。 用於將多個版本的資產運送至不同版本的 Visual Studio。 需要 Visual Studio 2017.3 或更新版本才會生效。

  - `AnyAttribute*`-在執行時間以名稱/值配對字典公開的一組開放式屬性。

    `<AnyElement>*`- `<Asset>`開始和結束標記之間允許任何結構化內容。 所有元素都是以 XmlElement 物件清單的形式公開。 VSIX 擴充功能可以在資訊清單檔中定義結構化類型特有的中繼資料, 並在執行時間進行列舉。

### <a name="sample-manifest"></a>範例資訊清單

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

- [寄送 Visual Studio 延伸模組](../extensibility/shipping-visual-studio-extensions.md)
