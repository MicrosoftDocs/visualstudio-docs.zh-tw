---
title: 開發 SharePoint 方案 |Microsoft Docs
description: 開發 SharePoint 方案。 知道 SharePoint 專案的元素。 瞭解 SharePoint 專案和專案專案屬性。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2f085f5679db2c5c4a1e3cf0cc8d7bbf7cad58eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948826"
---
# <a name="develop-sharepoint-solutions"></a>開發 SharePoint 方案
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中提供數個 SharePoint 專案類型範本，以用來建立 SharePoint 網站和網站元素。 如需可用專案類型的清單，請參閱 [SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。 以下是 SharePoint 專案的元素和屬性描述。

 如需 SharePoint 2013 與 SharePoint 增益集的相關資訊，請參閱 [SharePoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) 與 [建置 SharePoint 增益集](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)。

## <a name="elements-of-a-sharepoint-project"></a>SharePoint 專案的元素
 SharePoint 專案下方的節點稱為 *「SharePoint 項目」*(SharePoint item)。 SharePoint 項目也可能會包含一個以上的子檔案，稱為 *「SharePoint 項目檔案」*(SharePoint item file)，例如 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 組態檔、.aspx 表單等等。

 若不使用已填入專案項目檔案的專案範本來建立專案，您可以使用 [空專案]  範本來建立空白的 SharePoint 專案，然後手動加入專案項目。 SharePoint 專案也可以選擇性地包含一或多個功能檔案 (用於在 SharePoint 中啟用) 和用來散發專案的套件檔案。

### <a name="special-nodes"></a>特殊節點
 每個 SharePoint 專案皆包含兩個節點，您無法重新命名、刪除、剪下、複製或從專案拖曳這兩個節點。 以下為這兩個節點：

- 功能
- 套件

  即使專案沒有定義任何功能或套件，這兩個節點仍會出現在所有 SharePoint 專案中。

#### <a name="features-node"></a>功能節點
 [功能]  節點包含一或多個 SharePoint 專案功能。 每種功能都是 SharePoint 擴充功能的容器。 將功能部署至 SharePoint 伺服器之後，它可以包含在網站定義中或由 SharePoint 網站上的 SharePoint 系統管理員個別啟用。 如需詳細資訊，請參閱 [使用功能](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14))。

 當您將內容類型或清單執行個體這類項目加入 SharePoint 專案時，會將其加入 [功能]  節點中的一項功能。 而項目範圍可決定要將它加入新的或現有的功能。 如果新項目和現有功能具有相同的範圍，就會將其加入該功能。 若否，就會將該項目加入新的功能。

 若要手動新增功能，請在功能節點的捷徑功能表上執行 [加入功能]  命令。 您可以使用功能設計工具來檢視或變更功能的內容。 如需詳細資訊，請參閱 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。

 將功能加入 SharePoint 專案時，它會顯示為 [方案總管]  中的節點，並使用預設節點名稱：Feature *x*.feature，其中 *x* 是唯一的編號。 將功能部署至 SharePoint 伺服器之後，SharePoint 系統管理員可以啟動它，以讓 SharePoint 網站的使用者使用。

#### <a name="package-node"></a>封裝節點
 [套件]  節點包含單一檔案，以做為 SharePoint 專案的散發機制。 這個檔案稱為「 *方案套件*」。以 CAB 為基礎。WSP 延伸模組。 方案套件是一種可部署並重複使用的檔案，其中包含套用至 SharePoint 網站而可個別啟用或停用的一組功能、網站定義和組件。 同樣地，[套件]  節點一定會包含名為 Package.wspdef 的檔案，其為套件的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 定義檔。 將套件部署到執行 SharePoint 的伺服器之後，SharePoint 系統管理員即可加以安裝並啟用其功能。

 您可以按兩下套件節點或開啟其快捷方式功能表，然後選擇 [ **開啟**]，以在封裝設計工具中查看或變更封裝的內容。 如需詳細資訊，請參閱 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint 專案和專案專案屬性
 SharePoint 專案就像其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案一樣，會在 [屬性] 視窗和 [屬性] 頁面中顯示相關屬性。 所顯示的屬性視所選取的節點而定。

 在 [方案總管] 中選取 SharePoint 專案、專案項目或專案項目檔案節點時，[屬性] 視窗或 [屬性] 頁面會顯示下列屬性：

### <a name="project-properties"></a>專案屬性

|屬性名稱|描述|
|-------------------|-----------------|
|現用部署組態|指定於部署期間執行的步驟序列。 如需詳細資訊，請參閱 [如何：編輯 SharePoint 部署](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)設定。|
|組件部署目標|決定 *「SharePoint 應用程式組件」* (SharePoint application assembly) 所在位置。 有效的組件位置值為 *GlobalAssemblyCache* (預設值) 或 *WebApplication*。<br /><br /> 如果 *Sandboxed Solution* 屬性設為 **true**，就會停用這個屬性。|
|偵錯後自動撤銷|指定已部署的方案在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯模式中執行應用程式之後，是否會自動從 SharePoint 中撤銷。 若選取此項目，當 IDE 偵錯後回到設計檢視時，即會撤銷方案。 若清除此項目，就不會撤銷方案。 如需詳細資訊，請參閱 [撤銷解決方案](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14))。|
|編輯組態|指定要用於專案的部署組態。 如需詳細資訊，請參閱 [如何：編輯 sharepoint 部署](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 設定和 [部署、發行和升級 sharepoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。|
|啟用 Silverlight 偵錯 (而不是指令碼偵錯)|選取時，會將 Silverlight 偵錯工具附加至偵錯程序。 清除時，會將指令碼偵錯工具附加至偵錯程序。 如需詳細資訊，請參閱 [Silverlight 偵錯概觀](/previous-versions/windows/)。|
|在套件中包含組件|指定是否要在建置階段封裝專案的組件。|
|部署後命令列|指定要在部署 SharePoint 方案之後執行的命令。 此命令列支援任何批次命令，以及 MSBuild 變數的解析。 如需詳細資訊，請參閱 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。|
|預先部署命令列|指定要在部署 SharePoint 方案之前執行的命令。 此命令列支援任何批次命令，以及 MSBuild 變數的解析。 如需詳細資訊，請參閱 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。|
|專案檔|包含關於專案建置、組態與其他資訊之檔案的名稱。|
|專案資料夾|專案檔的系統位置。 (唯讀)。|
|Sandboxed Solution|指定是否應該將專案部署為 *「沙箱化方案」*(sandboxed solution)，也就是 *使用者建立的方案*。 沙箱化方案不一定值得信任。 **true** 值表示專案會部署為沙箱化方案，而 **false** 值表示專案會部署為陣列方案。 如需詳細資訊，請參閱 [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) 與 [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。|
|網站 URL|指定這個專案的目標網站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 。|
|啟動項目|指定要執行之專案中的第一個項目。|

 當您選擇 SharePoint 項目檔案 (例如工作流程或 [功能] 節點中的功能) 時，[屬性] 視窗中會顯示下列屬性：

### <a name="project-item-properties"></a>專案專案屬性

|屬性名稱|描述|
|-------------------|-----------------|
|部署衝突解決|指定在部署專案項目時，如果其屬性與伺服器上已經存在的項目相同，所應採取的動作。 如需詳細資訊，請參閱 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。|
|功能屬性|指定一組值 (儲存為索引鍵/值組)，當部署至 SharePoint 時，這些值會隨附在功能當中。 部署功能之後，您可以在程式碼中存取屬性值。 如需詳細資訊，請參閱 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|功能接收器|提供當專案項目所含的功能發生特定事件時，要執行的程式碼。 如需詳細資訊，請參閱 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|資料夾名稱|SharePoint 專案項目資料夾的名稱。|
|專案輸出參考|指定相依性，例如您的專案項目需要執行的組件。 如需詳細資訊，請參閱 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|安全控制項項目|指定可讓不受信任的使用者編輯的控制項。 如需詳細資訊，請參閱 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|

### <a name="project-item-file-properties"></a>專案專案檔案屬性

|屬性名稱|描述|
|-------------------|-----------------|
|建置動作|指定檔案與組建和部署處理序相關聯的方式。 如需詳細資訊，請參閱 [檔案屬性](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))。|
|複製到輸出目錄|指定是否要將原始程式檔複製到輸出目錄。 可以是下列值之一：<br /><br /> -   *不要複製*<br />-   *一律複製*<br />-   *如果更新則進行複製*<br /><br /> 如需詳細資訊，請參閱 [檔案屬性](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))。|
|自訂工具|指定工具的名稱 (如果有的話)，以在設計階段轉換檔案，並將轉換的輸出放入另一個檔案。 例如，資料集 (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) 檔案具有預設的自訂工具。 如需詳細資訊，請參閱 [檔案屬性](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))。|
|自訂工具命名空間|會將自訂工具的輸出複製到其中的命名空間。 如需詳細資訊，請參閱 [檔案屬性](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\))。|
|部署位置|檔案在 SharePoint 伺服器中的完整路徑。 這個路徑是由部署根和部署路徑的子屬性構成。|
|部署路徑|SharePoint 伺服器檔案上檔案的相對路徑，例如 Workflow1.xaml \\ 。 將 *Deployment Path* 值串連至 *Deployment Root* 值的結尾，即可建立檔案的完整路徑。<br /><br /> 選取 [*部署類型*] 屬性的 [ *RootFile* ] 值會將 *部署根* 屬性變更為 \<SharePointRoot> \\ ，以產生完整路徑的 \<SharePointRoot> \Workflow1 \\ 。 如需詳細資訊，請參閱 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)。|
|Deployment Root|字串。 在 SharePoint 伺服器部署檔案的根資料夾。 例如， \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ 。<br /><br /> *Deployment Root* 屬性值是依據 *Deployment Type* 設定而定。|
|部署類型|檔案的部署類型會決定其 *Deployment Root* 值。 可以是下列值之一：<br /><br /> NoDeployment *\<no value>*<br /><br /> ElementManifest： *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> ElementFile： *\<SharePointRoot> \\ \<FeatureName> \Template\Features \\*<br /><br /> TemplateFile： *\<SharePointRoot> \Template \\*<br /><br /> RootFile *\<SharePointRoot>\\*<br /><br /> GlobalResource： *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource *\<ClassResourcePath>\\*<br /><br /> 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.SharePoint.DeploymentType>。|
|檔案名稱|項目檔案的檔案或資料夾名稱。|
|完整路徑|項目檔案的位置。 (唯讀)。|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)|說明 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中提供的 SharePoint 專案和專案項目範本。|
|[如何：將項目新增至 SharePoint 專案](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|說明如何將新的或現有的項目加入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案。|
|[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|逐步引導您建立自訂欄位、內容類型、清單定義和清單執行個體。|
|[如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)|描述如何加入在 [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)中所建立之專案的事件接收器。|
|[建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)|說明如何建立工作流程專案，其中包含工作流程關聯表單和工作流程初始表單。|
|[建立 SharePoint 的頁面](../sharepoint/creating-pages-for-sharepoint.md)|說明如何建立頁面，例如 SharePoint 應用程式頁面、網站頁面、主版頁面和頁面配置。|
|[建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)|說明如何加入控制項，以讓使用者直接使用瀏覽器修改 SharePoint 網頁的內容、外觀及行為。|
|[為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|說明如何針對在 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用的使用者控制項。|
|[將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|說明如何將資料從 Web 服務和後端伺服器應用程式整合至 SharePoint 應用程式。|
|[建立 SharePoint 的網站定義](../sharepoint/creating-site-definitions-for-sharepoint.md)|說明如何建立網站定義，也就是用來建立 SharePoint 網站的範本。|
|[從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|說明如何從現有的 SharePoint 網站將內容類型和模組等項目匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案。|
|[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)|說明如何使用模組，以從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案將檔案部署至 SharePoint 網站。|
|[使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|說明如何使用伺服器總管瀏覽本機 SharePoint 網站。|
|[提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|說明如何使用專案項目屬性來提供專案的封裝和部署資訊，例如安全的控制項項目、專案輸出參考以及功能屬性等資訊。|
|[如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)|說明如何將對應的資料夾加入專案，以提供更容易存取 SharePoint 資源。|
|[沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)|說明與沙箱化方案相關聯的問題。|
|[SharePoint 方案的安全性](../sharepoint/security-for-sharepoint-solutions.md)|說明在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中開發 SharePoint 方案的安全性考量。|
|[URL 選擇器對話方塊 &#40;Visual Studio 中的 SharePoint 開發&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|說明可用來在您的專案或本機 SharePoint 伺服器上新增資源路徑參考的對話方塊。|

## <a name="see-also"></a>另請參閱
- [在 Visual Studio&#41;中開始 &#40;SharePoint 開發 ](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
