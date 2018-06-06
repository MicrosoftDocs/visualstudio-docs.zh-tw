---
title: 建立項目範本和專案範本之 SharePoint 專案項目的 |Microsoft 文件
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
ms.openlocfilehash: b789072b7a9cc84965e3d78a412631120783b40b
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765200"
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>建立項目範本和專案範本的 SharePoint 專案項目
  當您定義自訂 SharePoint 專案項目類型時，您可以將它與項目範本或專案範本，讓其他開發人員可以使用 Visual Studio 中的專案項目。 您也可以建立範本的精靈。  
  
 例如，Visual Studio 不包含專案範本或將欄位加入至 SharePoint 網站的項目範本。 您可以定義 SharePoint 專案項目類型所代表的欄位，然後建構其他開發人員可以使用的欄位項目加入 SharePoint 專案項目範本。 或者，您可以建構專案範本，讓開發人員可以建立新的 SharePoint 專案，其中包含的欄位項目。 在這兩種情況下，您也可以提供開發人員使用您的範本時，會出現精靈。 此精靈可以從開發人員設定新的項目或專案來收集資訊。  
  
 項目範本和專案範本是 *.zip*檔案，其中包含由 Visual Studio 用來建立專案項目或專案的檔案。 如需項目範本和專案範本的基本概念的詳細資訊，請參閱[建立專案和項目範本](/visualstudio/ide/creating-project-and-item-templates)。  
  
## <a name="create-item-templates"></a>建立項目範本
 當您建立 SharePoint 專案項目的項目範本時，還有一些檔案，永遠是必要的和的特定類型的專案項目可能會使用的選擇性檔案。 如需示範如何定義 SharePoint 專案項目類型，並為其建立的項目範本的逐步解說，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
 下表列出必要的檔案，以建立 SharePoint 專案項目的項目範本。  
  
|必要檔案|描述|  
|-------------------|-----------------|  
|*.Spdata*檔案|這是 XML 檔案，指定的內容和專案項目的預設行為。 這個檔案必須包含在項目範本。 如需有關內容 *.spdata*檔，請參閱[SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)。|  
|A *.vstemplate*檔案。|這個檔案提供 Visual Studio 顯示中的範本所需的資訊**加入新項目** 對話方塊，並從範本建立專案項目。 這個檔案必須包含在項目範本。 如需詳細資訊，請參閱[Visual Studio 範本中繼資料檔案](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面。|這個組件定義的執行的階段行為的專案項目。 這個組件必須包含在 VSIX 封裝包含項目範本。 如需詳細資訊，請參閱[定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)和[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。|  
  
 下表列出一些最常見的選擇性檔案可以包含在項目範本。 某些類型的專案項目可能需要其他檔案未列於此處。  
  
|選用的檔案|描述|  
|-------------------|-----------------|  
|*Elements.xml*|A*功能項目*檔案。 此檔案會定義 UI 和專案項目所建立的自訂行為。 每種類型的自訂，例如清單執行個體、 內容類型或自訂動作，會有不同的結構描述會定義這個檔案的內容。 如需詳細資訊，請參閱[建置組塊： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)和[功能結構描述](http://go.microsoft.com/fwlink/?LinkId=169192)。|  
|*Schema.xml*|如需清單定義結構描述檔案。 如需詳細資訊，請參閱[建置組塊： 清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=177792)和[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)。|  
|*.webpart*|A *Web 組件定義*檔案。 這個檔案包含 Web 組件的屬性設定。 如需詳細資訊，請參閱[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=177791)。|  
|*.ascx*|ASP.NET 使用者控制項檔案。 此檔案會定義視覺 Web 組件的 UI。|  
|*.aspx*|ASP.NET 網頁檔案中。 此檔案包含定義應用程式頁面上的 XML 標記。|  
|*.cs*或 *.vb*檔案|這些程式碼檔案會定義有程式設計模型，您可以從 Visual C# 或 Visual Basic 程式碼，例如應用程式頁面、 Web 組件和工作流程存取的 SharePoint 自訂的行為。|  
## <a name="create-project-templates"></a>建立專案範本
 當您建立 SharePoint 專案範本時，有部分永遠是必要和選擇性的特定類型的專案可能會使用的檔案的檔案。 一般而言，SharePoint 專案包含至少一個 SharePoint 專案項目。 不過，這不是必要。 例如，您可以定義要只能用來部署其他專案中建立 SharePoint 方案的 SharePoint 專案範本。  
  
 如需示範如何定義 SharePoint 專案項目類型，並為其建立專案範本的逐步解說，請參閱[逐步解說： 使用專案範本，第 1 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。  
  
 下表列出必須在 SharePoint 專案範本中包含的檔案。  
  
|必要檔案|描述|  
|-------------------|-----------------|  
|A *.vstemplate*檔案|這個檔案提供 Visual Studio 顯示中的範本所需的資訊**新專案** 對話方塊，並從範本建立專案。 如需詳細資訊，請參閱[Visual Studio 範本中繼資料檔案](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|A *.csproj*或 *.vbproj*檔案|這是專案檔。 它會定義的內容和專案的組態設定。|  
|*中*|此檔案會定義專案的部署封裝。 當您使用封裝設計工具自訂方案套件專案時，Visual Studio 會在這個檔案中儲存方案套件的相關資料。<br /><br /> 當您建立自訂 SharePoint 專案範本時，我們建議您包含只有最小必要的內容中*中*檔和您在使用中的 Api 來設定方案套件<xref:Microsoft.VisualStudio.SharePoint.Packages>命名空間中的專案範本相關聯的擴充功能。 如果您這樣做，您的專案範本被保護以免受到未來變更的結構*中*檔案。 如需範例，示範如何建立*中*檔案所需的最小與內容，請參閱[逐步解說： 使用專案範本，第 1 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要修改*中*直接檔案中，您可以使用在結構描述，以驗證內容 *%Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd*.|  
|*Package.Template.xml*|這個檔案提供方案的資訊清單檔案的基礎 (*manifest.xml*) 的 SharePoint 方案套件 (*.wsp*) 從專案所產生。 如果您想要指定某些並不適合您的專案類型的使用者變更的行為，您可以將內容加入此檔案。 如需詳細資訊，請參閱[建置組塊： 方案](http://go.microsoft.com/fwlink/?LinkId=169186)和[方案結構描述](http://go.microsoft.com/fwlink/?LinkId=177794)。<br /><br /> 當您建置方案套件專案時，Visual Studio 會合併的內容*中*和*Package.Template.xml*到解決方案的檔案資訊清單檔案。 如需建置方案套件的詳細資訊，請參閱[How to： 建立 SharePoint 方案套件 (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
 下表列出可以包含在專案範本的選擇性檔案。  
  
|選用的檔案|描述|  
|-------------------|-----------------|  
|SharePoint 專案項目|您可以包含一或多個.spdata 檔案定義 SharePoint 專案項目類型。 每個 *.spdata*檔案必須具有相符<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>VSIX 封裝專案範本中包含的延伸模組組件中實作。 如需詳細資訊，請參閱[建立項目範本](#creatingitemtemplates)。<br /><br /> 一般而言，SharePoint 專案包含至少一個 SharePoint 專案項目。 不過，這不是必要。|  
|*{featureName}.feature*|此檔案會定義用來部署多個專案項目是 SharePoint 功能。 當您使用功能設計工具來自訂您的專案中的功能時，Visual Studio 會儲存此檔案中功能的相關資料。 如果您想要的專案項目分組為不同的功能，您可以包含多個 *.feature*檔案。<br /><br /> 當您建立自訂 SharePoint 專案範本時，我們建議您在每個包含只有最小的所需的內容 *.feature*檔和您在使用中的 Api 來設定功能<xref:Microsoft.VisualStudio.SharePoint.Features>中的命名空間專案範本相關聯的延伸模組。 如果您這樣做，您的專案範本被保護以免受到未來變更的結構 *.feature*檔案。 如需範例，示範如何建立 *.feature*檔案所需的最小與內容，請參閱[逐步解說： 使用專案範本，第 1 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果您想要修改 *.feature*直接檔案中，您可以使用在結構描述，以驗證內容 *%Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*。|  
|*{featureName)。Template.xml*|這個檔案提供的基礎功能資訊清單檔案 (*這個*) 針對每個產生從專案的功能。 如果您想要指定某些並不適合您的專案類型的使用者變更的行為，您可以將內容加入此檔案。 如需詳細資訊，請參閱[建置組塊： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)和[這個](http://go.microsoft.com/fwlink/?LinkId=177795)檔案。<br /><br /> 當您建置方案套件專案時，Visual Studio 會合併的每一對內容 *{featureName}.feature*檔案和 *{featureName}。Template.xml*檔案到功能資訊清單檔案。 如需建置方案套件的詳細資訊，請參閱[How to： 建立 SharePoint 方案套件 (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
## <a name="create-wizards-for-item-templates-and-project-templates"></a>建立項目範本和專案範本的精靈
 您定義 SharePoint 專案項目類型，並將它與項目或專案範本產生關聯之後，您也可以建立精靈。 此精靈會顯示當開發人員會使用項目範本加入專案時，SharePoint 專案項目或開發人員可使用專案範本來建立新的專案，其中包含 SharePoint 專案項目。 開發人員從收集資訊，並初始化新的 SharePoint 專案項目，可以使用精靈。  
  
 如需示範如何建立項目範本和專案範本的精靈的逐步解說，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[逐步解說： 建立站台資料行專案項目，使用專案範本，第 2 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## <a name="see-also"></a>另請參閱
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說： 建立自訂動作專案項目包含項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [逐步解說： 建立網站欄專案項目以專案範本，第 1 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [建立專案和項目範本](/visualstudio/ide/creating-project-and-item-templates)  
  
 