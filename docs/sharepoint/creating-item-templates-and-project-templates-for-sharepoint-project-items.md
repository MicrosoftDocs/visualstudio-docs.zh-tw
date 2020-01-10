---
title: SharePoint 專案專案的專案範本/專案範本
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981167"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>為 SharePoint 專案專案建立專案範本和專案範本

當您定義自訂 SharePoint 專案專案類型時，可以將它與專案範本或專案範本產生關聯。 此關聯可讓其他開發人員使用 Visual Studio 中的專案專案。 您也可以建立範本的 wizard。

例如，Visual Studio 不包含將欄位加入至 SharePoint 網站的專案範本或專案範本。 您可以定義代表欄位的 SharePoint 專案專案類型，然後再建立其他開發人員可用來將欄位專案加入至 SharePoint 專案的專案範本。 或者，您可以建立專案範本，讓開發人員可以建立具有欄位專案的新 SharePoint 專案。 在這兩種情況下，您也可以提供當開發人員使用您的範本時所顯示的 wizard。 此 wizard 可以向開發人員收集資訊，以設定新的專案或專案。

專案範本和專案範本是 *.zip*檔案，其中包含 Visual Studio 用來建立專案專案或專案的檔案。 如需專案範本和專案範本基本概念的詳細資訊，請參閱[建立專案和專案範本](../ide/creating-project-and-item-templates.md)。

## <a name="create-item-templates"></a>建立項目範本
 當您建立 SharePoint 專案專案的專案範本時，一定會有一些檔案是必要的，有些則是特定專案專案類型可能使用的選擇性檔案。 如需示範如何定義 SharePoint 專案專案類型並為其建立專案範本的逐步解說，請參閱[逐步解說：使用專案範本建立自訂動作專案專案，第1部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。

 下表列出為 SharePoint 專案專案建立專案範本所需的檔案。

|必要檔案|描述|
|-------------------|-----------------|
|*.Spdata*檔案|這個 XML 檔案會指定專案專案的內容和預設行為。 這個檔案必須包含在專案範本中。 如需有關 *.spdata*檔內容的詳細資訊，請參閱[SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)。|
|*.Vstemplate*檔案。|這個檔案會提供 Visual Studio，其中包含在 [**加入新專案**] 對話方塊中顯示範本所需的資訊，以及從範本建立專案專案。 這個檔案必須包含在專案範本中。 如需詳細資訊，請參閱[Visual Studio 範本中繼資料](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))檔。|
|執行 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的 Visual Studio 延伸模組元件。|這個元件會定義專案專案的執行時間行為。 此元件必須包含在具有專案範本的 VSIX 封裝中。 如需詳細資訊，請參閱[定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)和[在 Visual Studio 中部署 SharePoint 工具的延伸](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)模組。|

 下表列出可以包含在專案範本中的一些最常見的選擇性檔案。 某些類型的專案專案可能需要此處未列出的其他檔案。

| 選擇性檔案 | 描述 |
|----------------------| - |
| *元素 .xml* | *功能元素*檔案。 這個檔案會定義專案專案所建立之自訂的 UI 和行為。 每種類型的自訂（例如清單實例、內容類型或自訂動作）都有不同的架構，可定義此檔案的內容。 如需詳細資訊，請參閱[建立區塊：功能](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))和[功能架構](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))。 |
| *Schema .xml* | 清單定義的架構檔案。 如需詳細資訊，請參閱[建立區塊：清單和文件庫](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))和[架構 .xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14))。 |
| *. webpart* | *Web 元件定義*檔。 此檔案包含 Web 元件的屬性設定。 如需詳細資訊，請參閱[建立區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。 |
| *.ascx* | ASP.NET UserControl 檔案。 此檔案會定義視覺 Web 元件的 UI。 |
| *.aspx* | ASP.NET 網頁檔。 此檔案包含定義應用程式頁面的 XML 標記。 |
| *.cs*或 *.vb*檔案 | 這些程式碼檔案會定義 SharePoint 自訂的行為，而此程式設計模型可以從視覺C#效果或 Visual Basic 程式碼（例如應用程式頁面、Web 元件和工作流程）存取。 |

## <a name="create-project-templates"></a>建立專案範本
 當您建立 SharePoint 專案範本時，有一些檔案一律是必要的，以及特定專案類型可能使用的選擇性檔案。 一般來說，SharePoint 專案包含至少一個 SharePoint 專案專案。 不過，這不是必要的。 例如，您可以定義一個專門用來部署在其他專案中建立之 SharePoint 方案的 SharePoint 專案範本。

 如需示範如何定義 SharePoint 專案專案類型並為其建立專案範本的逐步解說，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。

 下表列出必須包含在 SharePoint 專案範本中的檔案。

|必要檔案|描述|
|-------------------|-----------------|
|*.Vstemplate*檔案|這個檔案會提供 Visual Studio，其中包含在 [**新增專案**] 對話方塊中顯示範本所需的資訊，以及從範本建立專案。 如需詳細資訊，請參閱[Visual Studio 範本中繼資料](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))檔。|
|*.Csproj*或 *. vbproj*檔案|這是專案檔案。 它會定義專案的內容和設定。|
|*Package. package*|此檔案會定義專案的部署套件。 當您使用 [封裝設計工具] 自訂專案的方案套件時，Visual Studio 會將解決方案封裝的相關資料儲存在此檔案中。<br /><br /> 當您建立自訂 SharePoint 專案範本時，我們建議您只在 Package 檔案中包含最少必要內容，並使用擴充功能中的 <xref:Microsoft.VisualStudio.SharePoint.Packages> 命名空間中的 Api 來設定方案套件 *。* 與專案範本相關聯。 如果您這樣做，您的專案範本會受到保護，使其無法日後變更*封裝的結構。封裝*檔案。 如需示範如何建立*封裝*檔案的範例，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要直接修改*封裝*檔案，可以使用 *% Program Files （x86）% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*的架構來驗證內容。|
|*Package. Template .xml*|這個檔案會針對從專案產生的 SharePoint 方案套件（ *.wsp*），提供方案資訊清單檔案（*manifest .xml*）的基礎。 如果您想要指定某些不打算由專案類型的使用者變更的行為，您可以將內容新增至這個檔案。 如需詳細資訊，請參閱[建立區塊：方案](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14))和[方案架構](/sharepoint/dev/schema/solution-schema)。<br /><br /> 當您從專案建立方案套件時，Visual Studio 會將*封裝*的內容和封裝 *.xml*檔案合併到方案資訊清單檔中。 如需建立方案套件的詳細資訊，請參閱[如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。|

 下表列出可以包含在專案範本中的選擇性檔案。

|選擇性檔案|描述|
|-------------------|-----------------|
|SharePoint 專案項目|您可以包含一個或多個定義 SharePoint 專案專案類型的 .spdata 檔案。 在具有專案範本的 VSIX 封裝中，每個 *.spdata*檔案都必須具有相符的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 實作為延伸元件。 如需詳細資訊，請參閱[建立專案範本](#create-item-templates)。<br /><br /> 一般來說，SharePoint 專案包含至少一個 SharePoint 專案專案。 不過，這不是必要的。|
|*\<功能特性 >。*|這個檔案會定義用來將數個專案專案分組以進行部署的 SharePoint 功能。 當您使用 [功能設計工具] 自訂專案中的功能時，Visual Studio 會將此功能的相關資料儲存在此檔案中。 如果您想要將專案專案分組成不同的功能，您可以包含多個*功能*檔案。<br /><br /> 當您建立自訂 SharePoint 專案範本時，建議您只在每個功能檔案中包含最小的必要內容，並使用與相關聯之延伸模組的 <xref:Microsoft.VisualStudio.SharePoint.Features> 命名空間中的 Api 來設定功能 *。* 專案範本。 如果您這樣做，您的專案範本會受到保護，以防止未來變更*功能*檔案的結構。 如需示範如何建立只含最小必要內容的*功能*檔案的範例，請參閱[逐步解說：使用專案範本建立網站資料行專案專案，第1部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要直接修改*功能*檔案，您可以使用 *% Program Files （x86）% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*的架構來驗證內容。|
|*\<功能 >。範本 .xml*|此檔案提供從專案產生之每項功能的功能資訊清單檔案（*feature .xml*）基礎。 如果您想要指定某些不打算由專案類型的使用者變更的行為，您可以將內容新增至這個檔案。 如需詳細資訊，請參閱[建立區塊：功能](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))和[功能 .xml](/sharepoint/dev/schema/feature-xml-files)檔案。<br /><br /> 當您從專案建立方案套件時，Visual Studio 會將每一對\<\<*功能 >* 的內容合併在一起。 *範本 .xml*檔案放入功能資訊清單檔案中。 如需建立方案套件的詳細資訊，請參閱[如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>建立專案範本和專案範本的嚮導
 定義 SharePoint 專案專案類型，並將它與專案或專案範本產生關聯之後，您也可以建立 wizard。 當開發人員使用專案範本將 SharePoint 專案專案加入至專案時，或當開發人員使用專案範本來建立包含 SharePoint 專案專案的新專案時，會顯示此 wizard。 此 wizard 可用來向開發人員收集資訊，以及初始化新的 SharePoint 專案專案。

 如需示範如何為專案範本和專案範本建立嚮導的逐步解說，請參閱[逐步解說：使用專案範本建立自訂動作專案專案、第2部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[逐步解說：使用專案建立網站資料行專案專案範本，第2部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

## <a name="see-also"></a>請參閱

- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
