---
title: VSIX 延伸架構2.0 參考 |Microsoft Docs
description: VSIX 延伸架構2.0 會定義 VSIX 部署資訊清單檔的檔案格式，以描述 VSIX 封裝的內容。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2edd0349555380f6d98d24f7a40c22e48797d12
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863762"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 延伸架構2.0 參考
VSIX 部署資訊清單檔案會描述 VSIX 封裝的內容。 檔案格式是由架構所控管。 此架構的版本2.0 支援新增自訂類型和屬性。  資訊清單的架構是可擴充的。 資訊清單載入器會忽略其不了解的 XML 元素和屬性。

> [!IMPORTANT]
> Visual Studio 2015 可以載入 Visual Studio 2010、Visual Studio 2012 或 Visual Studio 2013 格式的 VSIX 檔案。

## <a name="package-manifest-schema"></a>封裝資訊清單架構
 資訊清單 XML 檔案的根項目為 `<PackageManifest>` 。 它具有單一屬性 `Version` ，也就是資訊清單格式的版本。 如果對格式進行了重大變更，則版本格式會變更。 本文描述資訊清單格式版本2.0，這是在資訊清單中指定，其方式是將 `Version` 屬性設定為 version = "2.0" 的值。

### <a name="packagemanifest-element"></a>PackageManifest 元素
 在 `<PackageManifest>` 根項目中，您可以使用下列元素：

- `<Metadata>` -有關封裝本身的中繼資料和廣告資訊。 `Metadata`資訊清單中只允許有一個元素。

- `<Installation>` -這個區段會定義此延伸模組套件的安裝方式，包括可安裝至其中的應用程式 Sku。 `Installation`資訊清單中只允許單一元素。 資訊清單必須有 `Installation` 元素，否則此套件不會安裝在任何 SKU 中。

- `<Dependencies>` -此封裝的選擇性相依性清單定義于此處。

- `<Assets>` -此區段包含此套件中包含的所有資產。 如果沒有此區段，此套件將不會呈現任何內容。

- `<AnyElement>*` -資訊清單架構有足夠的彈性可允許任何其他元素。 資訊清單載入器無法辨識的任何子項目都會在擴充管理員 API 中公開為額外的 XmlElement 物件。 VSIX 擴充功能可以使用這些子項目，在資訊清單檔中定義其他資料，在 Visual Studio 中執行的程式碼可以在執行時間存取。 請參閱 [VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120))。

### <a name="metadata-element"></a>Metadata 元素
 此區段是關於套件、其身分識別和廣告資訊的中繼資料。 `<Metadata>` 包含下列元素：

- `<Identity>` -定義此封裝的識別資訊，並包含下列屬性：

  - `Id` -此屬性必須是其作者所選擇之套件的唯一識別碼。 名稱的限定方式與 CLR 類型的命名空間： Company.Product.Feature.Name。 `Id`屬性的限制為100個字元。

  - `Version` -定義此封裝的版本及其內容。 這個屬性會遵循 CLR 元件版本控制格式： 1.2.40308.00) 的 (。 版本號碼較高的套件會被視為套件的更新，並可安裝在現有安裝的版本上。

  - `Language` -此屬性是封裝的預設語言，而且會對應到此資訊清單中的文字資料。 這個屬性會遵循資源元件的 CLR 地區設定程式碼慣例，例如： en-us、en、fr。 您可以指定 `neutral` ，宣告將在任何版本的 Visual Studio 上執行的語言中性延伸模組。 預設值是 `neutral`。

  - `Publisher` -此屬性會識別此封裝的發行者（公司或個別名稱）。 `Publisher`屬性的限制為100個字元。

- `<DisplayName>` -這個元素會指定在擴充管理員 UI 中顯示的易記套件名稱。 `DisplayName`內容的限制為50個字元。

- `<Description>` -此選擇性專案是封裝的簡短描述，以及顯示在 [擴充管理員] UI 中的內容。 `Description`內容可以包含任何您想要的文字，但限制為1000個字元。

- `<MoreInfo>` -這個選擇性元素是包含此封裝完整描述的頁面線上 URL。 通訊協定必須指定為 HTTP。

- `<License>` -這個選擇性專案是套件中所含的授權檔案 ( .txt、.rtf) 的相對路徑。

- `<ReleaseNotes>` -這個選擇性專案是封裝中包含的版本資訊檔案的相對路徑 ( .txt、.rtf) 或顯示版本資訊的網站 URL。

- `<Icon>` -這個選擇性元素是封裝中所含之影像檔案 (png、bmp、jpeg、.ico) 的相對路徑。 圖示影像應為32x32 圖元 (或會壓縮為該大小) ，並顯示在 listview UI 中。 如果未 `Icon` 指定任何元素，則 UI 會使用預設值。

- `<PreviewImage>` -這個選擇性元素是封裝中所含之影像檔案 (png、bmp、jpeg) 的相對路徑。 預覽影像應為200x200 圖元，並顯示在詳細資料 UI 中。 如果未 `PreviewImage` 指定任何元素，則 UI 會使用預設值。

- `<Tags>` -這個選擇性元素會列出用於搜尋提示的其他以分號分隔的文字標記。 `Tags`元素的限制為100個字元。

- `<GettingStartedGuide>` -這個選擇性專案是 HTML 檔案的相對路徑或網站的 URL，其中包含如何使用此套件中的延伸模組或內容的相關資訊。 本指南是在安裝過程中啟動的。

- `<AnyElement>*` -資訊清單架構有足夠的彈性可允許任何其他元素。 資訊清單載入器無法辨識的任何子項目都會公開為 XmlElement 物件的清單。 VSIX 擴充功能可以使用這些子項目，在資訊清單檔中定義其他資料，並在執行時間列舉它們。

### <a name="installation-element"></a>安裝元素
 本節定義此封裝的安裝方式，以及可安裝的應用程式 Sku。 此區段包含下列屬性：

- `Experimental` -如果您目前有針對所有使用者安裝的延伸模組，但您在同一部電腦上開發更新的版本，請將這個屬性設定為 true。 例如，如果您已為所有使用者安裝 MyExtension 1.0，但您想要在同一部電腦上偵測 MyExtension 2.0，請設定實驗 = "true"。 這個屬性可在 Visual Studio 2015 Update 1 和更新版本中使用。

- `Scope` -此屬性可以採用 "Global" 或 "ProductExtension" 值：

  - "Global" 指定安裝的範圍不限於特定的 SKU。 例如，安裝延伸模組 SDK 時，會使用這個值。

  - "ProductExtension" 指定在安裝個別 Visual Studio Sku (版本 1.0) 的傳統 VSIX 擴充功能。 這是預設值。

- `AllUsers` -這個選擇性屬性會指定是否要為所有使用者安裝此封裝。 根據預設，這個屬性為 false，指定封裝為每位使用者。  (當您將此值設定為 true 時，安裝的使用者必須提升為系統管理許可權層級，才能安裝所產生的 VSIX。

- `InstalledByMsi` -這個選擇性屬性會指定 MSI 是否安裝此封裝。 Msi 安裝的封裝是由 MSI (程式和功能所安裝及管理，而不是由 Visual Studio 延伸模組管理員所) 。  根據預設，這個屬性為 false，指定 MSI 不會安裝封裝。

- `SystemComponent` -這個選擇性屬性會指定是否應將此封裝視為系統元件。 系統元件不會顯示在擴充管理員 UI 中，而且無法更新。 根據預設，這個屬性為 false，指定封裝不是系統元件。

- `AnyAttribute*` - `Installation` 元素接受一組開放式的屬性，這些屬性會在執行時間公開為名稱/值組字典。

- `<InstallationTarget>` -此元素控制 VSIX 安裝程式安裝封裝的位置。 如果屬性的值 `Scope` 為 "ProductExtension"，則套件必須以 SKU 為目標，該 SKU 已安裝資訊清單檔案作為其內容的一部分，以通告其對延伸模組的可用性。 `<InstallationTarget>`當 `Scope` 屬性具有明確或預設值 "ProductExtension" 時，元素會有下列屬性：

  - `Id` -此屬性可識別套件。  屬性遵循命名空間慣例： Company.Product.Feature.Name。 `Id`屬性只能包含英數位元，且限制為100個字元。 預期的值：

    - VisualStudio. IntegratedShell

    - Microsoft.VisualStudio.Pro

    - VisualStudio Premium

    - VisualStudio 旗艦版

    - VisualStudio. VWDExpress

    - VisualStudio. VPDExpress

    - VisualStudio. VSWinExpress

    - VisualStudio. VSLS

    - 我的 Shell. 應用程式

  - `Version` -此屬性會使用此 SKU 的最小和最大支援版本來指定版本範圍。 封裝可以詳細說明它支援的 Sku 版本。 版本範圍標記法是 [10.0-11.0]，其中

    - [-最小版本（含）。

    - ]-最大版本（含）。

    -  (-最小版本專屬。

    - ) -最大版本專屬。

    - 單一版本 #-僅限指定的版本。

    > [!IMPORTANT]
    > Visual Studio 2012 引進了 VSIX 架構的2.0 版。 若要使用此架構，您必須在電腦上安裝 Visual Studio 2012 或更新版本，並使用屬於該產品的 VSIXInstaller.exe。 您可以使用 Visual Studio 2012 或更新版本 VSIXInstaller 的舊版 Visual Studio，但只能使用更新版本的安裝程式。

    您可以在 [Visual Studio 組建編號和發行日期](../install/visual-studio-build-numbers-and-release-dates.md)找到 Visual Studio 2017 版號碼。

    當表示 Visual Studio 2017 版本的版本時，次要版本應該一律為 **0**。 例如，Visual Studio 2017 15.3.26730.0 版應以 [15.0.26730.0，16.0) 表示。 只有 Visual Studio 2017 和更新版本號碼才需要這項功能。

  - `AnyAttribute*` - `<InstallationTarget>` 元素允許在執行時間公開為名稱/值組字典的開放式屬性集。

### <a name="dependencies-element"></a>相依性元素
 這個元素包含這個封裝所宣告的相依性清單。 如果指定了任何相依性，其)  (識別的封裝 `Id` 必須已安裝之前。

- `<Dependency>` 元素-這個子項目具有下列屬性：

  - `Id` -此屬性必須是相依套件的唯一識別碼。 這個識別值必須符合 `<Metadata><Identity>Id` 此封裝相依的封裝屬性。 `Id`屬性遵循命名空間慣例： Company.Product.Feature.Name。 屬性只能包含英數位元，且限制為100個字元。

  - `Version` -此屬性會使用此 SKU 的最小和最大支援版本來指定版本範圍。 封裝可以詳細說明它支援的 Sku 版本。 版本範圍標記法是 [12.0，13.0]，其中：

    - [-最小版本（含）。

    - ]-最大版本（含）。

    -  (-最小版本專屬。

    - ) -最大版本專屬。

    - 單一版本 #-僅限指定的版本。

  - `DisplayName` -此屬性是相依封裝的顯示名稱，用於 UI 元素，例如對話方塊和錯誤訊息。 除非 MSI 已安裝相依的封裝，否則此屬性是選擇性的。

  - `Location` -這個選擇性屬性會將此 VSIX 中的相對路徑指定為嵌套 VSIX 封裝，或指定相依性下載位置的 URL。 這個屬性是用來協助使用者找出必要條件套件。

  - `AnyAttribute*` - `Dependency` 元素接受一組開放式的屬性，這些屬性會在執行時間公開為名稱/值組字典。

### <a name="assets-element"></a>資產元素
 這個元素包含 `<Asset>` 此封裝所呈現的每個延伸模組或內容元素的標記清單。

- `<Asset>` -這個元素包含下列屬性和元素：

  - `Type` -此元素所表示的延伸或內容類型。 每個 `<Asset>` 元素都必須有一個 `Type` ，但多個 `<Asset>` 元素可能相同 `Type` 。 這個屬性應該根據命名空間慣例，以完整名稱表示。 已知的類型為：

    1. VisualStudio. VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. VisualStudio. ToolboxControl

    4. VisualStudio 範例

    5. VisualStudio. ProjectTemplate

    6. VisualStudio

    7. VisualStudio. 元件

       您可以建立自己的類型，並提供它們唯一的名稱。 在 Visual Studio 內的執行時間，您的程式碼可以透過延伸模組管理員 API 來列舉和存取這些自訂類型。

  - `Path` -包含資產之套件內的檔案或資料夾的相對路徑。

  - `TargetVersion` -套用指定資產的版本範圍。 用來將多個版本的資產傳送至不同版本的 Visual Studio。 需要 Visual Studio 2017.3 或更新版本才會生效。

  - `AnyAttribute*` -在執行時間公開為名稱/值組字典的開放式屬性集。

    `<AnyElement>*` -開始與結束標記之間允許任何結構化內容 `<Asset>` 。 所有元素都會公開為 XmlElement 物件的清單。 VSIX 擴充功能可以在資訊清單檔中定義結構化類型專屬的中繼資料，並在執行時間列舉它們。

### <a name="sample-manifest"></a>資訊清單範例

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

## <a name="see-also"></a>請參閱

- [寄送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
