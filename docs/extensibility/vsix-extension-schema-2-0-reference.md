---
title: "VSIX 擴充功能 2.0 結構描述參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f0ac6fdedb5d65f40f718c568297dc0196c4537
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 擴充功能 2.0 結構描述參考
VSIX 部署資訊清單檔描述 VSIX 套件的內容。 檔案格式是結構描述所決定。 此結構描述的 2.0 版支援的自訂類型和屬性加入。  資訊清單的結構描述可以延伸。 資訊清單的載入器會忽略不了解的 XML 元素和屬性。  
  
> [!IMPORTANT]
>  Visual Studio 2015 可以載入 Visual Studio 2010、 Visual Studio 2012 或 Visual Studio 2013 格式 VSIX 檔案。  
  
## <a name="package-manifest-schema"></a>封裝資訊清單結構描述  
 資訊清單 XML 檔案的根項目是`<PackageManifest>`，具有單一屬性`Version`，這是資訊清單的格式版本。 如果主要變更格式，將變更的版本格式。 本主題描述資訊清單的格式版本 2.0 中，設定來指定資訊清單中`Version`屬性值的版本為 ="2.0"。  
  
### <a name="packagemanifest-element"></a>PackageManifest 項目  
 內`<PackageManifest>`根項目，您可以使用下列項目：  
  
-   `<Metadata>`中繼資料和廣告資訊封裝本身。 只有一個`Metadata`元素可在資訊清單中。  
  
-   `<Installation>`-此區段會定義這個擴充套件可供安裝包括應用程式可以安裝中的 Sku 的方式。 只有一個`Installation`元素可在資訊清單中。 資訊清單必須`Installation`項目或此封裝將不會安裝到任何 SKU。  
  
-   `<Dependencies>`-此處會定義此封裝的相依性的選擇性清單。  
  
-   `<Assets>`-這個區段包含所有必要資產，包含此套件中。 本節中，沒有此套件不會出現任何內容。  
  
-   `<AnyElement>*`-資訊清單結構描述是有足夠的彈性，以允許其他項目。 擴充管理員 API 中公開的資訊清單的載入器無法識別任何子項目為額外的 XmlElement 物件。 使用這些子元素，VSIX 擴充功能可以在 Visual Studio 中執行的程式碼可以存取在執行階段的資訊清單檔案中定義其他資料。 請參閱<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A>和<xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>。  
  
### <a name="metadata-element"></a>中繼資料元素  
 此區段是封裝、 其身分識別，和廣告資訊的相關中繼資料。 `<Metadata>`包含下列元素：  
  
-   `<Identity>`-這會定義此套件識別資訊，並包含下列屬性：  
  
    -   `Id`-這個屬性必須是其作者所選封裝的唯一識別碼。 名稱必須符合規定的 CLR 型別是已命名空間的相同方式： Company.Product.Feature.Name。 `Id`屬性僅限於 100 個字元。  
  
    -   `Version`-這會定義這個封裝和其內容的版本。 這個屬性會遵循 CLR 組件版本控制格式： Major.Minor.Build.Revision (1.2.40308.00)。 具有較高的版本號碼的套件會被視為對套件的更新，而且可以透過現有的安裝版本安裝。  
  
    -   `Language`-這個屬性是封裝的預設語言，且對應到此資訊清單中的文字資料。 這個屬性會遵循 CLR 地區設定程式碼慣例資源組件，例如： en-us-我們、 en-us、 為 fr-fr。 您可以指定`neutral`宣告任何版本的 Visual Studio 會執行非語言相關擴充功能。 預設值是 `neutral`。  
  
    -   `Publisher`-這個屬性會識別此封裝，公司或名稱的個別的 「 發行者 」。 `Publisher`屬性僅限於 100 個字元。  
  
-   `<DisplayName>`-此項目會指定會顯示在擴充管理員 UI 中的使用者易記的封裝名稱。 `DisplayName`內容僅限於 50 個字元。  
  
-   `<Description>`-此選擇性項目是顯示在擴充管理員 UI 中的封裝和其內容的簡短描述。 `Description`內容可包含您想，但有任何文字限制為 1000年個字元。  
  
-   `<MoreInfo>`-此選擇性項目是網頁的 URL 連線，其中包含此套件的完整描述。 必須指定通訊協定為 http。  
  
-   `<License>`-此選擇性項目是包含在封裝中的授權檔案 （.txt、.rtf） 的相對路徑。  
  
-   `<ReleaseNotes>`-此選擇性項目是版本資訊檔案 （.txt、.rtf） 的套件，否則會顯示版本資訊的網站的 URL 中包含可能是相對路徑。  
  
-   `<Icon>`-此選擇性項目是包含在封裝中的映像檔案 （png、 bmp、 jpeg、 ico） 的相對路徑。 圖示影像應該是 32 x 32 像素 （或將會壓縮該大小），並出現在 listview UI。 如果沒有`Icon`項目未指定，UI 會使用預設值。  
  
-   `<PreviewImage>`-此選擇性項目是包含在封裝中的映像檔案 （png、 bmp、 jpeg） 的相對路徑。 預覽影像應該是 200 x 200 像素，並顯示在 UI 的詳細資料。 如果沒有`PreviewImage`項目未指定，UI 會使用預設值。  
  
-   `<Tags>`-此選擇性項目會列出用於搜尋提示的其他以分號分隔的文字標籤。 `Tags`項目是限制為 100 個字元。  
  
-   `<GettingStartedGuide>`-此選擇性項目為 HTML 檔案的相對路徑，或是包含如何使用擴充功能或此套件中的內容的相關資訊的網站的 URL。 本指南是以安裝的一部分來啟動。  
  
-   `<AnyElement>*`-資訊清單結構描述是有足夠的彈性，以允許其他項目。 資訊清單的載入器無法辨識任何子項目會公開為一份 XmlElement 物件。 使用這些子元素，VSIX 擴充功能可以資訊清單檔中定義的其他資料，並在執行階段加以列舉。  
  
### <a name="installation-element"></a>安裝項目  
 這個區段會定義可以安裝此套件的方式，而且它可以安裝到應用程式 Sku。 本節包含下列屬性：  
  
-   `Experimental`-將此屬性設為 true，如果您有目前已安裝所有的使用者擴充功能，但您正在開發的同一部電腦上的更新的版本。 例如，如果您已安裝 MyExtension 1.0 的所有使用者，但您想要在同一部電腦上偵錯 MyExtension 2.0，將實驗 ="true"。 這個屬性是可在 Visual Studio 2015 Update 1 及更新版本。  
  
-   `Scope`-這個屬性可以接受的值"Global"或"ProductExtension 」:  
  
    -   「 全域 」 指定安裝不以特定的 SKU 為範圍。 例如，安裝擴充功能 SDK 時，會使用此值。  
  
    -   「 ProductExtension 」 指定已安裝的傳統 VSIX 擴充功能 （1.0 版） 範圍設定為個別的 Visual Studio Sku。 這是預設值。  
  
-   `AllUsers`-此選擇性屬性會指定是否將針對所有使用者安裝此套件。 根據預設，這個屬性是 false，指定封裝是每位使用者。 （當您將此值設為 true 時，安裝的使用者必須提高為系統管理特殊權限來安裝產生 VSIX。  
  
-   `InstalledByMsi`-此選擇性屬性會指定此套件是否已安裝 MSI。 安裝和管理由 MSI （程式和功能） 和不由 Visual Studio 擴充功能管理員安裝 MSI 封裝。  根據預設，這個屬性是 false，指定 MSI 未安裝的套件。  
  
-   `SystemComponent`-此選擇性屬性會指定此套件是否應該視為系統元件。 不要在擴充管理員 UI 中顯示的系統元件，且無法更新。 根據預設，這個屬性是 false，指定封裝不是系統元件。  
  
-   `AnyAttribute*`-`Installation`元素接受屬性會公開在做為名稱-值配對字典的執行階段的開放集合。  
  
-   `<InstallationTarget>`-此項目會控制 VSIX 安裝程式會安裝封裝的位置。 如果值`Scope`屬性是 「 ProductExtension"封裝必須為目標的 SKU 的已安裝的資訊清單檔案做為它的內容公告其可用性，來擴充功能的一部分。 `<InstallationTarget>`項目具有下列屬性時`Scope`屬性具有明確或預設值"ProductExtension 」:  
  
    -   `Id`-這個屬性會識別封裝。  屬性會遵循的命名空間慣例： Company.Product.Feature.Name。 `Id`屬性只能包含英數字元，且僅限於 100 個字元。 預期值：  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version`-這個屬性會指定與此 SKU 的最小和最大支援版本的版本範圍。 封裝中可詳述的 Sku 支援的版本。 版本範圍標記為 [10.0-11.0] 其中  
  
        -   [-最小版本 （含）。  
  
        -   ]-最大版本 （含）。  
  
        -   (-獨佔的最小版本。  
  
        -   )-獨佔的最大版本。  
  
        -   單一版本 #-指定的版本。  
  
        > [!IMPORTANT]
        >  Visual Studio 2012 中引進了 VSIX 結構描述的 2.0 版。 若要使用此結構描述您必須安裝 Visual Studio 2012 或更新版本電腦上安裝並將 VSIXInstaller.exe 屬於該產品。 您可以針對較早版本的 Visual Studio 與 Visual Studio 2012 或更新版本的 VSIXInstaller，但只能透過使用較新版本的安裝程式。  
  
    -   `AnyAttribute*`-`<InstallationTarget>`項目可讓屬性會公開在做為名稱-值配對字典的執行階段的開放集合。  
  
### <a name="dependencies-element"></a>相依性項目  
 這個項目包含此套件會宣告的相依性清單。 如果未指定任何相依性，這些封裝 (由其`Id`) 必須是前已安裝。  
  
-   `<Dependency>`項目-這個子項目具有下列屬性：  
  
    -   `Id`-這個屬性必須是相依套件的唯一識別碼。 此身分識別值必須符合`<Metadata><Identity>Id`屬性，此套件所依存的封裝。 `Id`屬性遵循的命名空間慣例： Company.Product.Feature.Name。 屬性只能包含英數字元，且僅限於 100 個字元。  
  
    -   `Version`-這個屬性會指定與此 SKU 的最小和最大支援版本的版本範圍。 封裝中可詳述的 Sku 支援的版本。 版本範圍表示法是非負數 [12.0，13.0]，位置：  
  
        -   [-最小版本 （含）。  
  
        -   ]-最大版本 （含）。  
  
        -   (-獨佔的最小版本。  
  
        -   )-獨佔的最大版本。  
  
        -   單一版本 #-指定的版本。  
  
    -   `DisplayName`-UI 項目，例如對話方塊和錯誤訊息中使用的相依套件的顯示名稱這個屬性。 屬性是選擇性的除非由 MSI 安裝相依的套件。  
  
    -   `Location`-此選擇性屬性會指定此 VSIX，巢狀的 VSIX 套件內的相對路徑或相依性的下載位置的 URL。 此屬性用來協助找出的必要條件封裝的使用者。  
  
    -   `AnyAttribute*`-`Dependency`元素接受屬性會公開在做為名稱-值配對字典的執行階段的開放集合。  
  
### <a name="assets-element"></a>資產項目  
 這個項目包含一份`<Asset>`這個封裝所提出的每個擴充功能或內容項目的標記。  
  
-   `<Asset>`-此元素包含下列屬性和項目：  
  
    -   `Type`-這是擴充功能或表示由這個項目內容的型別。 每個`<Asset>`項目必須具有單一`Type`，但多個`<Asset>`項目可能有相同`Type`。 根據命名空間慣例，應該為完整格式名稱，表示這個屬性。 已知型別如下：  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         您可以建立自己的型別，並指定其唯一的名稱。 在 Visual Studio 內的執行階段，您的程式碼可以列舉並透過 擴充管理員 API 存取這些自訂的類型。  
  
    -   路徑的檔案或資料夾，其中包含資產封裝內的相對路徑。  
  
    -   `AnyAttribute*`的屬性會公開在做為名稱 / 值組字典的執行階段開放集合。  
  
         `<AnyElement>*`-任何結構化的內容之間允許`<Asset>`開頭和結尾標記。 所有的項目都會公開為一份 XmlElement 物件。 VSIX 擴充功能可以定義資訊清單檔中的結構化之特定類型的中繼資料，並在執行階段加以列舉。  
  
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
  
## <a name="see-also"></a>請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)