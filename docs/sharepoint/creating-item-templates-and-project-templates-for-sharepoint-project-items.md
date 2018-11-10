---
title: 建立項目範本和專案範本的 SharePoint 專案項目 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d181891fb36645e4f246aa0c2238c12ea1dc4903
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296004"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>建立項目範本和專案範本，為 SharePoint 專案項目
  當您定義自訂的 SharePoint 專案項目類型時，則您可以將它與項目範本或專案範本。 此關聯可讓其他開發人員使用 Visual Studio 中的專案項目。 您也可以建立範本的精靈。

 例如，Visual Studio 不會包含專案範本或將欄位加入至 SharePoint 網站的項目範本。 您可以定義 SharePoint 專案項目類型表示的欄位，並再建構其他開發人員可用來將欄位項目新增至 SharePoint 專案項目範本。 或者，您可以建構專案範本，好讓開發人員可以建立新的 SharePoint 專案的欄位項目。 在這兩種情況下，您也可以提供一個精靈，開發人員使用您的範本時，會出現。 此精靈可以從 設定新的項目或專案的開發人員收集資訊。

 項目範本和專案範本都 *.zip*包含 Visual studio 用來建立專案項目或專案檔案的檔案。 如需項目範本和專案範本的基本概念的詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。

## <a name="create-item-templates"></a>建立項目範本
 當您建立 SharePoint 專案項目的項目範本時，有一些檔案，一向是必要的和特定類型的專案項目可能使用的選擇性檔案。 如需示範如何定義 SharePoint 專案項目類型，並為它建立的項目範本的逐步解說，請參閱 <<c0> [ 逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。

 下表列出必要的檔案，以建立 SharePoint 專案項目的項目範本。

|必要檔案|描述|
|-------------------|-----------------|
|*.Spdata*檔案|此 XML 檔案指定的內容和專案項目的預設行為。 這個檔案必須包含在項目範本。 如需有關的內容 *.spdata*檔，請參閱[SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)。|
|A *.vstemplate*檔案。|此檔案會提供 Visual Studio 中顯示範本中的所需的資訊**加入新項目** 對話方塊中，並從範本建立專案項目。 這個檔案必須包含在項目範本。 如需詳細資訊，請參閱 < [Visual Studio 範本中繼資料檔案](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))。|
|Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面。|這個組件定義的執行的階段行為的專案項目。 這個組件必須包含在 VSIX 封裝，包含項目範本。 如需詳細資訊，請參閱 <<c0> [ 定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)並[部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。|

 下表列出一些最常見的選擇性檔案可以包含在項目範本。 某些類型的專案項目可能需要其他這裡未列出的檔案。


| 選用的檔案 | 描述 |
|----------------------| - |
| *Elements.xml* | A *Feature 元素*檔案。 此檔案會定義 UI 和專案項目所建立的自訂行為。 每一種自訂，例如清單執行個體、 內容類型或自訂動作，會有不同的結構描述會定義這個檔案的內容。 如需詳細資訊，請參閱 <<c0> [ 建置組塊： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)並[功能結構描述](http://go.microsoft.com/fwlink/?LinkId=169192)。 |
| *Schema.xml* | 清單定義結構描述檔案。 如需詳細資訊，請參閱 <<c0> [ 建置組塊： 清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=177792)並[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)。 |
| *.webpart* | A *Web 組件定義*檔案。 此檔案包含在 Web 組件的屬性設定。 如需詳細資訊，請參閱 <<c0> [ 建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=177791)。 |
| *.ascx* | ASP.NET 使用者控制項檔案。 此檔案會定義視覺 Web 組件的 UI。 |
| *.aspx* | ASP.NET 網頁檔案中。 此檔案包含定義應用程式頁面的 XML 標記。 |
| *.cs*或是 *.vb*檔案 | 這些程式碼檔案會定義具有的程式設計模型，您可以從 Visual C# 或 Visual Basic 程式碼，例如應用程式頁面、 Web 組件和工作流程存取 SharePoint 自訂行為。 |

## <a name="create-project-templates"></a>建立專案範本
 當您建立 SharePoint 專案範本時，有一些總是必要和選擇性的特定類型的專案可能會使用的檔案的檔案。 一般而言，SharePoint 專案包含至少一個 SharePoint 專案項目。 不過，這是不必要。 例如，您可以定義要只能用來部署在其他專案中建立 SharePoint 方案的 SharePoint 專案範本。

 如需示範如何定義 SharePoint 專案項目類型，並為它建立的專案範本的逐步解說，請參閱 <<c0> [ 逐步解說： 使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。

 下表列出必須在 SharePoint 專案範本中包含的檔案。

|必要檔案|描述|
|-------------------|-----------------|
|A *.vstemplate*檔案|此檔案會提供 Visual Studio 中顯示範本中的所需的資訊**新的專案** 對話方塊中，並從範本建立專案。 如需詳細資訊，請參閱 < [Visual Studio 範本中繼資料檔案](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))。|
|A *.csproj*或是 *.vbproj*檔案|這是專案檔。 它會定義的內容和專案的組態設定。|
|*封裝*|此檔案會定義專案的部署套件。 當您使用封裝設計工具自訂專案的方案套件時，Visual Studio 會儲存此檔案中的方案套件的相關資料。<br /><br /> 當您建立自訂的 SharePoint 專案範本時，我們建議您加入只有最小必要的內容中*封裝*檔案，以及您在使用中的 Api 來設定的方案套件<xref:Microsoft.VisualStudio.SharePoint.Packages>在專案範本與相關聯的擴充功能中的命名空間。 如果您這麼做，您的專案範本受到未來變更的結構*封裝*檔案。 如需範例，示範如何建立*封裝*檔案只需要最少內容，請參閱[逐步解說： 使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要修改*封裝*直接檔案中，您可以使用之結構描述，以確認內容 *%Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|這個檔案提供的基礎方案的資訊清單檔案 (*manifest.xml*) 的 SharePoint 方案套件 (*.wsp*)，從專案中產生。 如果您想要指定某些不是要變更您的專案類型的使用者的行為，您可以將內容到這個檔案。 如需詳細資訊，請參閱 <<c0> [ 建置組塊： 方案](http://go.microsoft.com/fwlink/?LinkId=169186)並[解決方案結構描述](http://go.microsoft.com/fwlink/?LinkId=177794)。<br /><br /> 當您建置專案的方案套件時，Visual Studio 會將合併的內容*封裝*並*Package.Template.xml*到解決方案的檔案資訊清單檔案。 如需建置方案套件的詳細資訊，請參閱 <<c0> [ 如何： 使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。|

 下表列出可以包含在專案範本的選擇性檔案。

|選用的檔案|描述|
|-------------------|-----------------|
|SharePoint 專案項目|您可以包含一或多個.spdata 檔案可定義 SharePoint 專案項目型別。 每個 *.spdata*檔案必須具有相符<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>VSIX 封裝專案範本中包含的延伸模組組件中的實作。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本](#creatingitemtemplates)。<br /><br /> 一般而言，SharePoint 專案包含至少一個 SharePoint 專案項目。 不過，這是不必要。|
|*\<featureName >.feature*|此檔案會定義用來分組進行部署的數個專案項目是 SharePoint 功能。 當您使用功能設計工具在您的專案中自訂功能時，Visual Studio 會在這個檔案中儲存之功能的相關資料。 如果您想要的專案項目分組為不同的功能，您可以包含多個 *.feature*檔案。<br /><br /> 當您建立自訂的 SharePoint 專案範本時，我們建議您將只有最少的必要的內容包含在每個 *.feature*檔案，以及您在使用中的 Api 來設定功能<xref:Microsoft.VisualStudio.SharePoint.Features>中的命名空間專案範本與相關聯的延伸模組。 如果您這麼做，您的專案範本受到未來變更的結構 *.feature*檔案。 如需範例，示範如何建立 *.feature*檔案只需要最少內容，請參閱[逐步解說： 使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要修改 *.feature*直接檔案中，您可以使用之結構描述，以確認內容 *%Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*。|
|*\<featureName >。Template.xml*|這個檔案提供的基礎功能資訊清單檔案 (*Feature.xml*) 從專案產生的每項功能。 如果您想要指定某些不是要變更您的專案類型的使用者的行為，您可以將內容到這個檔案。 如需詳細資訊，請參閱 <<c0> [ 建置組塊： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)並[Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795)檔案。<br /><br /> 當您建置專案的方案套件時，Visual Studio 的內容合併至每個成對 *\<featureName >.feature*檔案並 *\<featureName >。Template.xml*檔案載入功能資訊清單檔案。 如需建置方案套件的詳細資訊，請參閱 <<c0> [ 如何： 使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>建立項目範本和專案範本的精靈
 您定義 SharePoint 專案項目類型和其關聯的項目或專案範本之後，您也可以建立精靈。 此精靈會顯示當開發人員將 SharePoint 專案項目加入至專案中，使用項目範本，或當開發人員使用的專案範本來建立新的專案，其中包含 SharePoint 專案項目。 從開發人員收集資訊，並初始化新的 SharePoint 專案項目，則可以使用精靈。

 如需示範如何建立項目範本和專案範本的精靈的逐步解說，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[逐步解說： 建立網站使用專案範本，第 2 部分的資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

## <a name="see-also"></a>另請參閱

- [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [逐步解說： 使用專案範本，第 1 部分中建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [逐步解說： 使用專案範本，第 2 部分中建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
