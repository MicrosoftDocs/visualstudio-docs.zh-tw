---
title: VSIX 延伸結構描述 2.0 參考 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf013f24f38485d0db1ec6ca9f45d26f2ede2c9f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684737"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 延伸結構描述 2.0 參考
VSIX 部署資訊清單檔描述 VSIX 封裝的內容。 檔案格式是結構描述所決定。 此結構描述的 2.0 版支援的自訂型別和屬性加入。  資訊清單的結構描述是 「 可延伸的。 它並不了解的 XML 元素和屬性，則會忽略資訊清單的載入器。

> [!IMPORTANT]
>  Visual Studio 2015 可以載入 Visual Studio 2010 中，Visual Studio 2012 或 Visual Studio 2013 格式中的 VSIX 檔案。

## <a name="package-manifest-schema"></a>封裝資訊清單結構描述
 資訊清單的 XML 檔案的根項目是`<PackageManifest>`。 它具有單一屬性`Version`，這是資訊清單的格式版本。 如果格式進行重要變更，則會變更的版本格式。 本文說明資訊清單的格式版本 2.0 中，指定資訊清單中，藉由設定`Version`屬性版本的值 ="2.0"。

### <a name="packagemanifest-element"></a>PackageManifest 項目
 內`<PackageManifest>`根項目，您可以使用下列項目：

-   `<Metadata>` 中繼資料，封裝本身的廣告資訊。 只有一個`Metadata`元素可在資訊清單中。

-   `<Installation>` -此區段會定義此延伸模組套件可以安裝，包括它可以安裝到應用程式 Sku 的方式。 只有一個`Installation`元素可在資訊清單中。 資訊清單必須有`Installation`項目，則此封裝將不會安裝到任何 SKU。

-   `<Dependencies>` -此處會定義此套件的相依性的選擇性清單。

-   `<Assets>` -本章節包含的所有包含此套件中的資產。 本節中，沒有此套件不會出現任何內容。

-   `<AnyElement>*` -資訊清單的結構描述是有足夠的彈性，以允許任何其他項目。 資訊清單的載入器無法辨識的任何子項目會擴充管理員 API 中公開為額外的 XmlElement 物件。 使用這些子元素，VSIX 擴充功能可以在 Visual Studio 中執行的程式碼可以存取在執行階段之資訊清單檔案中定義其他資料。 請參閱 <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> 和 <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>。

### <a name="metadata-element"></a>中繼資料元素
 本節是封裝、 其身分識別，以及廣告資訊的相關中繼資料。 `<Metadata>` 包含下列元素：

-   `<Identity>` -定義此套件的識別資訊，並包含下列屬性：

    -   `Id` -此屬性必須是其作者所選封裝的唯一識別碼。 CLR 型別是命名空間的相同方式，應該限定名稱：Company.Product.Feature.Name. `Id`屬性會限制為 100 個字元。

    -   `Version` -定義此套件和其內容的版本。 這個屬性會遵循 CLR 組件版本控制格式：Major.Minor.Build.Revision (1.2.40308.00)。 具有較高的版本號碼的套件會被視為更新套件，並可以透過現有的安裝版本安裝。

    -   `Language` -此屬性為預設的語言套件，並對應到此資訊清單中的文字資料。 這個屬性會遵循 CLR 的地區設定的程式碼慣例資源組件，例如： en-us-我們、 en、 fr-fr。 您可以指定`neutral`宣告會在任何版本的 Visual Studio 執行的非語言相關延伸模組。 預設值為 `neutral`。

    -   `Publisher` -此屬性會識別此套件的公司 」 或 「 個別名稱的 「 發行者 」。 `Publisher`屬性會限制為 100 個字元。

-   `<DisplayName>` -此項目會指定擴充管理員 UI 中顯示的使用者易記的封裝名稱。 `DisplayName`內容僅限於 50 個字元。

-   `<Description>` -此選擇性項目是顯示在 擴充管理員 UI 中的封裝和其內容的簡短描述。 `Description`內容可以包含任何文字，但其限制為 1000年個字元。

-   `<MoreInfo>` -此選擇性項目是網頁的 URL 連線，其中包含此套件的完整描述。 必須指定通訊協定為 http。

-   `<License>` -此選擇性項目是包含在套件中的授權檔案 （.txt、.rtf） 的相對路徑。

-   `<ReleaseNotes>` -此選擇性項目時的相對路徑 （.txt、.rtf） 的套件，否則不要顯示版本資訊的網站的 URL 中包含版本資訊檔案。

-   `<Icon>` -此選擇性項目是包含在套件中的映像檔案 （png、 bmp、 jpeg、 ico） 的相對路徑。 圖示影像應該是 32 x 32 像素 （或將會壓縮該大小），並出現在 listview UI。 如果沒有`Icon`指定項目時，UI 會使用預設值。

-   `<PreviewImage>` -此選擇性項目是包含在套件中的映像檔案 （png、 bmp、 jpeg） 的相對路徑。 預覽影像應為 200x200 的像素，而顯示在 UI 的詳細資料。 如果沒有`PreviewImage`指定項目時，UI 會使用預設值。

-   `<Tags>` -此選擇性項目會列出用於搜尋提示的其他以分號分隔的文字標籤。 `Tags`項目是限制為 100 個字元。

-   `<GettingStartedGuide>` -此選擇性項目為 HTML 檔案的相對路徑，或是包含如何使用延伸模組或是此套件中的內容的相關資訊的網站的 URL。 本指南就會啟動為安裝的一部分。

-   `<AnyElement>*` -資訊清單的結構描述是有足夠的彈性，以允許任何其他項目。 資訊清單的載入器無法辨識的任何子項目都會公開為一份 XmlElement 物件。 使用這些子元素，VSIX 擴充功能可以在資訊清單檔案中定義其他資料，並列舉它們在執行階段。

### <a name="installation-element"></a>安裝項目
 此區段會定義可以安裝此套件的方式和它可以安裝到應用程式 Sku。 本節包含下列屬性：

-   `Experimental` -設定這個屬性為 true，如果您有針對所有使用者，目前已安裝的延伸模組，但您正在開發的同一部電腦上的更新的版本。 例如，如果您已安裝 MyExtension 1.0 的所有使用者，但您想要在同一部電腦上偵錯 MyExtension 2.0，請將設定實驗性 ="true"。 這個屬性是可在 Visual Studio 2015 Update 1 及更新版本。

-   `Scope` -這個屬性可以接受的值"Global"或"ProductExtension 」:

    -   「 全域 」 指定的安裝不限於特定的 SKU。 比方說，在安裝擴充功能 SDK 時，會使用此值。

    -   「 ProductExtension"會指定已安裝的是傳統的 VSIX 擴充 （1.0 版） 範圍設定為個別的 Visual Studio Sku。 這是預設值。

-   `AllUsers` -此選擇性屬性會指定是否會針對所有使用者安裝此套件。 根據預設，此屬性為 false，表示封裝是每位使用者。 （當您將此值為 true 時，安裝的使用者必須提高為系統管理員權限層級，若要安裝產生的 VSIX。

-   `InstalledByMsi` -此選擇性屬性會指定此套件是否已安裝 MSI。 安裝和管理由 MSI （程式和功能） 及不由 Visual Studio 延伸模組管理員安裝 msi 套件。  根據預設，此屬性為 false，表示 MSI 未安裝封裝。

-   `SystemComponent` -此選擇性屬性會指定此套件是否應該視為系統元件。 系統元件不會顯示在 擴充管理員 UI，而且無法更新。 根據預設，此屬性為 false，以指定封裝不是系統元件。

-   `AnyAttribute*` -`Installation`元素接受的屬性會公開在做為名稱 / 值組字典的執行階段的開放集合。

-   `<InstallationTarget>` -此項目會控制 VSIX 安裝程式會安裝套件的位置。 如果值`Scope`屬性是 「 ProductExtension"封裝必須為目標的 SKU，已安裝的資訊清單檔做為它的內容公告其可用性，可延伸模組的一部分。 `<InstallationTarget>`項目具有下列屬性`Scope`屬性已明確或預設值"ProductExtension 」:

    -   `Id` -此屬性會識別封裝。  屬性會遵循命名空間慣例：Company.Product.Feature.Name. `Id`屬性只能包含英數字元，且上限為 100 個字元。 預期的值：

        -   Microsoft.VisualStudio.IntegratedShell

        -   Microsoft.VisualStudio.Pro

        -   Microsoft.VisualStudio.Premium

        -   Microsoft.VisualStudio.Ultimate

        -   Microsoft.VisualStudio.VWDExpress

        -   Microsoft.VisualStudio.VPDExpress

        -   Microsoft.VisualStudio.VSWinExpress

        -   Microsoft.VisualStudio.VSLS

        -   My.Shell.App

    -   `Version` -此屬性會指定與此 SKU 的最小和最大支援版本的版本範圍。 封裝中可詳述支援的 Sku 的版本。 版本範圍標記法，為 [10.0-11.0]，

        -   [-最低版本 （含）。

        -   ]-最高版本 （含）。

        -   (-獨佔的最小版本。

        -   )-獨佔的最大版本。

        -   單一版本 #-指定的版本。

        > [!IMPORTANT]
        >  2.0 版 VSIX 結構描述的是 Visual Studio 2012 中引進。 若要使用此結構描述您必須將 Visual Studio 2012 或稍後在電腦上安裝和使用是該產品的一部分 VSIXInstaller.exe。 您可以針對舊版的 Visual Studio 與 Visual Studio 2012 或更新版本的 VSIXInstaller，但只能透過使用較新版本的安裝程式。

        Visual Studio 2017 版本號碼，請參閱[Visual Studio 組建編號和發行日期](../install/visual-studio-build-numbers-and-release-dates.md)。

        Visual Studio 2017 的版本更新的版本時，次要的版本應該總是**0**。 Visual Studio 2017 版本 15.3.26730.0 比方說，應該以 [15.0.26730.0,16.0)。 這只是所需的 Visual Studio 2017 版本號碼。

    -   `AnyAttribute*` -`<InstallationTarget>`項目可讓在做為名稱 / 值組字典的執行階段會公開屬性的開放集合。

### <a name="dependencies-element"></a>相依性項目
 這個項目包含此套件會宣告的相依性清單。 如果未指定任何相依性，這些套件 (由其`Id`) 必須先安裝。

-   `<Dependency>` 項目-這個子項目具有下列屬性：

    -   `Id` -此屬性必須是相依的套件的唯一識別碼。 此身分識別值必須符合`<Metadata><Identity>Id`封裝這個封裝所相依的屬性。 `Id`屬性遵循的命名空間慣例：Company.Product.Feature.Name. 屬性只能包含英數字元，而且限制為 100 個字元。

    -   `Version` -此屬性會指定與此 SKU 的最小和最大支援版本的版本範圍。 封裝中可詳述支援的 Sku 的版本。 版本範圍標記法是 [12.0，13.0]，其中：

        -   [-最低版本 （含）。

        -   ]-最高版本 （含）。

        -   (-獨佔的最小版本。

        -   )-獨佔的最大版本。

        -   單一版本 #-指定的版本。

    -   `DisplayName` -此屬性是套件的相依會在 UI 項目，例如對話方塊和錯誤訊息的顯示名稱。 屬性是選擇性的除非相依的套件會安裝 MSI。

    -   `Location` -此選擇性屬性會指定此 VSIX，巢狀的 VSIX 套件內的相對路徑或相依性的下載位置的 URL。 這個屬性用來協助使用者找出必要的套件。

    -   `AnyAttribute*` -`Dependency`元素接受的屬性會公開在做為名稱 / 值組字典的執行階段的開放集合。

### <a name="assets-element"></a>資產的項目
 這個元素包含一份`<Asset>`這個封裝所呈現的標記每個擴充功能或內容的項目。

- `<Asset>` -此元素包含下列屬性和項目：

  - `Type` 延伸模組或此元素所代表的內容類型。 每個`<Asset>`項目必須具有單一`Type`，但多個`<Asset>`項目可能會有相同`Type`。 根據命名空間慣例都應為完整格式名稱，表示這個屬性。 已知的類型包括：

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       您可以建立自己的型別，並為它們提供唯一的名稱。 在 Visual Studio 內的執行階段，您的程式碼可以列舉並透過擴充管理員 API 來存取這些自訂的類型。

  - `Path` -檔案或資料夾包含資產之套件內的相對路徑。

  - `TargetVersion` -要套用指定的資產的版本範圍。 用來傳送多個版本的 Visual Studio 的不同版本的資產。 需要 Visual Studio 2017.3 或更新版本，才能產生的影響。

  - `AnyAttribute*` -屬性開放集合所公開的執行階段做為名稱 / 值組的字典。

     `<AnyElement>*` -任何結構化的內容之間不允許`<Asset>`開頭和結尾標記。 所有項目都會公開為一份 XmlElement 物件。 VSIX 擴充功能可以定義資訊清單檔中的結構化型別特定中繼資料，並列舉它們在執行階段。

### <a name="sample-manifest"></a>範例資訊清單

```
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
- [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
