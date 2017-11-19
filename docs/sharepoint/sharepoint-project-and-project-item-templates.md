---
title: "SharePoint 專案和專案項目範本 |Microsoft 文件"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 513b2216a99f37ba3aff1174965470b20921072f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 專案與專案項目範本
  下列各節說明可用的 SharePoint 專案和專案項目範本和使用方式。 
  
##  <a name="project-and-project-item-templates-overview"></a>專案和專案項目範本概觀  
 當您在 Visual Studio 中建立新的 SharePoint 專案時，以及所有專案項目，該專案類型所需方案加入 SharePoint 專案。 例如，如果您建立的 Silverlight Web 組件專案，Visual Studio 會建立包含視覺 Web 組件的專案項目和 Silverlight 應用程式專案項目，這些專案項目所需的所有檔案和方案。 專案項目範本用來將專案項目加入至現有的 SharePoint 專案，例如加入事件接收器、 站台的資料行或清單。  
  
 如需 SharePoint 基本概念資訊，請參閱[SharePoint Foundation 建置組塊](http://go.microsoft.com/fwlink/?LinkId=179404)。 進階的使用者可以建立自訂專案與專案項目範本。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
##  <a name="project-templates"></a>專案範本  
 以下是 SharePoint 專案範本的清單。 若要檢視在 Visual Studio 中的 SharePoint 專案範本中**新專案**對話方塊方塊中，展開  **SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**。  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 專案  
 內容*SharePoint 2010 專案*隨附的每個 SharePoint 專案範本。 SharePoint 2010 專案包含：  
  
-   專案檔。  
  
-   在專案屬性頁中。  
  
-   A**參考**資料夾列出所有在專案中的組件參考。  
  
-   A**功能**.feature 組態檔，用來將功能部署至 SharePoint 伺服器所在的資料夾。  
  
-   A**封裝**包含用來將方案部署到 SharePoint 中檔案的資料夾。  
  
-   Key.snk （強式名稱金鑰） 檔案用來簽署為強式名稱，組件的增強式安全性。  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight Web 組件  
 *SharePoint 2010 Silverlight Web 組件*專案可讓您建立顯示 Silverlight 應用程式的 SharePoint web 組件。 當您建立此專案時，您可以指定是否要加入新的 Silverlight 應用程式，或參考現有。 如需詳細資訊，請參閱[建立 sharepoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)和[逐步解說： 建立 SharePoint Silverlight Web 組件的顯示 OData](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覺 Web 組件  
 A *SharePoint 2010 視覺 Web 組件*專案包含 Elements.xml 檔案，位於定義， **Web 組件**項目，和**使用者控制項**項目。 您可以設計視覺 web 組件的外觀，拖曳或複製 Visual Studio 工具箱的控制項新增至使用者控制項的介面。 如需詳細資訊，請參閱[How to： 使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="import-sharepoint-2010-solution-package"></a>匯入 SharePoint 2010 方案套件  
 *匯入 SharePoint 2010 方案套件*專案可讓您匯入所有或部分現有的 SharePoint 2010 網站，匯出至 SharePoint 方案 (.wsp) 檔案，Visual studio。 在匯入 Visual Studio，您可以自訂其項目，並將其重新佈署。 如需詳細資訊，請參閱[匯入現有的 SharePoint 網站中的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>匯入可重複使用的 SharePoint 2010 工作流程  
 *匯入可重複使用的 SharePoint 2010 工作流程*專案可讓您匯入到 Visual Studio SharePoint Designer 2010 中建立可重複使用、 宣告式工作流程。 工作流程是從 SharePoint 網站匯出為.wsp 檔案。 在匯入 Visual Studio，可以自訂、 加入程式碼，並再將它部署至 SharePoint 網站。 如需詳細資訊，請參閱[逐步解說： 將 SharePoint Designer 可重複使用工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。  
  
##  <a name="project-item-templates"></a>專案項目範本  
 以下是 SharePoint 專案項目範本的清單。 專案項目範本會將檔案新增至 SharePoint 方案，以支援 SharePoint 功能，例如網站資料行、 清單和內容類型。 比方說，將網站資料行加入至您的方案將站台資料行專案包含 Elements.xml 定義檔。 新增視覺 web 組件將視覺 web 組件專案加入至您的方案包含 Elements.xml 檔案、 使用者控制項項目，以及視覺 web 組件項目。  
  
 若要檢視中的 SharePoint 專案項目範本，**方案總管 中**，開啟 SharePoint 專案的捷徑功能表，然後選擇**新增**，**新項目**。 展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**。  
  
### <a name="application-page-farm-solution-only"></a>應用程式頁面上 （僅限陣列方案）  
 **應用程式頁面上 （僅限陣列方案）**項目可讓您設計[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]SharePoint 網站的網頁。 應用程式頁面只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[How to： 建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)和[應用程式 _layouts 頁面類型](http://go.microsoft.com/fwlink/?LinkId=179434)。  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>商務資料連接模型 （僅限陣列方案）  
 A**商務資料連接模型 （僅限陣列方案）**項目可讓您將商業資料整合至 SharePoint。 商務資料可以來自後端伺服器應用程式，例如[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]、 Siebel 和服務廣告通訊協定 」 (SAP)。 商務資料連接模型只用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[How to： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)， [How to： 使用資源檔，以指定當地語系化名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，和[What's New： 商務連接服務](http://go.microsoft.com/fwlink/?LinkId=179411)。  
  
### <a name="content-type"></a>內容類型  
 *內容類型*項目可讓您建立根據現有的 （基底） 內容類型的文件、 通知或工作之類的自訂內容類型。 自訂內容類型會提供相同的屬性和欄位做為基底內容類型以及您定義任何網站資料行 （欄位）。 例如，您可以建立自訂的連絡人內容類型為基礎的基底的連絡人內容類型出現在 SharePoint 中。 您可以變更現有的網站資料行或新增更多站台的資料行已經包含在基底內容類型中的項目，以自訂的內容類型。  
  
> [!NOTE]  
>  由於 SharePoint 的限制，您無法建立沙箱化方案的內容類型為基礎的伺服器陣列的方案內容類型。  
  
 如需詳細資訊，請參閱[逐步解說： 建立網站資料行、 內容類型，以及 sharepoint 清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和[建置組塊： 內容類型](http://go.microsoft.com/fwlink/?LinkId=179413)。  
  
### <a name="empty-element"></a>空元素  
 *空元素*最常用於定義缺少專案或專案項目範本在 Visual Studio 中的 SharePoint 專案項目。 當您將空的項目加入至您的專案時，節點名為 EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] 包含名為 Elements.xml 單一檔案。 使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式，以在 Elements.xml 中定義的所需的項目。  
  
### <a name="event-receiver"></a>事件接收器  
 *事件接收器*處理事件的 SharePoint 網站，例如項目加入至清單中時，刪除 web 項目時，或當啟動工作流程中的項目。 事件接收器專案項目範本可讓您處理  
  
-   列出的事件  
  
-   清單項目事件  
  
-   列出的電子郵件事件  
  
-   Web 事件  
  
-   列出工作流程的事件  
  
 事件接收器專案項目建立**事件接收器**資料夾，並包含所有事件的事件處理常式，當您建立的專案中指定單一類別檔案**SharePoint 自訂精靈**。 事件接收器類別可以處理項目，例如檔案、 欄位、 項目、 清單、 附件、 web 組件和工作流程會新增、 更新、 刪除，或移除時，會發生在 SharePoint 網站的事件。 如需詳細資訊，請參閱[How to： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)和[建置組塊： 事件處理](http://go.microsoft.com/fwlink/?LinkId=179416)。  
  
### <a name="list"></a>清單  
 清單是可重複使用基底 SharePoint 清單定義，例如行事曆或工作清單中的執行個體。 將清單加入至您的方案之後, 清單設計工具可讓您將網站資料行加入至清單，並建立自訂清單的資料行。 這包括站台內容類型的資料行。 您可以指定*檢視*針對清單中，以決定將會出現在清單中的資料行。 如需詳細資訊，請參閱[逐步解說： 建立網站資料行、 內容類型，以及 sharepoint 清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和[建置組塊： 清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=179421)。  
  
### <a name="module"></a>模組  
 *模組*(不到與混淆[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]模組) 包含您想要部署到 SharePoint 伺服器，例如影像或資訊的任何檔案。 模組專案項目包含**模組**節點。 [模組] 節點包含兩個專案項目範本： XML 定義檔，做為模組資訊清單，以及 sample.txt 檔案預留位置檔案。 如需詳細資訊，請參閱[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)和[模組](http://go.microsoft.com/fwlink/?LinkId=179425)。  
  
### <a name="sequential-workflow-farm-solution-only"></a>循序工作流程 （僅限陣列方案）  
 A*循序工作流程*是一系列的最後一個步驟完成之前，依序執行的商務邏輯步驟。 循序工作流程可用來管理處理程序牽涉到 SharePoint 項目，例如清單和文件。 您可以建立站台層級 （全域） 工作流程或 (local) 工作流程清單層級，以及您可以選擇是否自動或手動啟動的工作流程。 這個專案項目只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流程](http://go.microsoft.com/fwlink/?LinkId=260555)，和[What's New： 工作流程改善](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="silverlight-web-part"></a>Silverlight Web 組件  
 *Silverlight web 組件*專案項目可讓您建立顯示 Silverlight 應用程式的 SharePoint web 組件。 當您將這個專案項目加入至您的方案時，您可以選擇是否要加入新的 Silverlight 應用程式或供稍後參考現有的我的最愛。 如需詳細資訊，請參閱[建立 sharepoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)和[逐步解說： 建立 SharePoint Silverlight Web 組件的顯示 OData](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="site-column"></a>網站資料行  
 A*網站資料行*，亦稱為*欄位*，是最基本的項目，您可以加入 SharePoint 專案的其中一個。 網站資料行代表資料類型，例如電話號碼、 文字註解，或是連絡人清單中連絡人的城市名稱。 如需詳細資訊，請參閱[建立網站資料行、 內容類型，以及 sharepoint 清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)和[資料行](http://go.microsoft.com/fwlink/?LinkId=226840)。  
  
### <a name="site-definition-farm-solution-only"></a>網站定義 （僅限陣列方案）  
 *站台定義*專案項目包含的站台定義資料夾，其中包含下列檔案：  
  
-   預設的.aspx 網頁，針對這個網站使用預設 web 網頁。  
  
-   定義站台元件的 onet.xml 檔案。  
  
-   指定出現在站台定義設定 webtemp xml 檔案**範本選擇**區段**新的 SharePoint 網站**頁面。  
  
 新增網站定義之後，您可以加入程式碼和引入功能檔案。 這個專案項目只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[建立 SharePoint 的站台定義](../sharepoint/creating-site-definitions-for-sharepoint.md)和[網站定義和設定](http://go.microsoft.com/fwlink/?LinkId=260554)。  
  
### <a name="state-machine-workflow-farm-solution-only"></a>狀態機器工作流程 （僅限陣列方案）  
 A*狀態機器工作流程*是一組商務邏輯狀態、 轉換和動作。 狀態機器工作流程中的步驟不能在序列中，執行相反地，它們便會觸發動作和狀態。 循序工作流程，例如狀態機器工作流程是 SharePoint 項目，例如清單和文件相關聯。 同樣地，您可以建立站台層級 （全域） 的工作流程或清單層級 （本機）。 您也可以選取是否自動或手動啟動的工作流程。 這個專案項目只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流程](http://go.microsoft.com/fwlink/?LinkId=260555)，和[What's New： 工作流程改善](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="user-control-farm-solution-only"></a>使用者控制項 （僅限陣列方案）  
 A*使用者控制項*是自訂、 可重複使用的控制項，您可以加入其他 ASP.NET 控制項和 SharePoint 控制項。 使用者控制可加入應用程式頁面和 web 組件，在 SharePoint 中執行。 這個專案項目只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱[Web 組件或應用程式頁面建立可重複使用控制項](http://go.microsoft.com/fwlink/?LinkId=226841)。  
  
### <a name="visual-web-part"></a>視覺 Web 組件  
 A*視覺 web 組件*專案項目中包括 Elements.xml 檔案，位於定義， **Web 組件**項目，和**使用者控制項**項目。 您可以設計視覺 web 組件的外觀，拖曳或複製 Visual Studio 工具箱的控制項新增至使用者控制項的介面。 如需詳細資訊，請參閱[How to： 使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="web-part"></a>網頁組件  
 A *web 組件*是一種特殊的頁面稱為網頁組件內執行的伺服器端控制項。 它們會出現在 SharePoint 網站的頁面的建置組塊。 Web 組件項目會提供可讓您設計的 SharePoint 網站的 web 組件的檔案。 如需詳細資訊，請參閱[How to： 建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)和[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
## <a name="see-also"></a>另請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 產品與技術](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
