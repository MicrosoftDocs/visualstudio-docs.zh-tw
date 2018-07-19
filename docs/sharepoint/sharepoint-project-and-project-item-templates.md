---
title: SharePoint 專案與專案項目範本 |Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ccff01afcb2556469453d4227b14ebe3b897de50
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118631"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 專案與專案項目範本
  下列各節說明可用的 SharePoint 專案和專案項目範本，以及如何使用它們。 
  
## <a name="project-and-project-item-templates-overview"></a>專案和專案項目範本概觀
 當您在 Visual Studio 中建立新的 SharePoint 專案時，以及所有專案項目，該專案類型所需的方案加入 SharePoint 專案。 比方說，如果您建立 Silverlight Web 組件專案，Visual Studio 會建立一個解決方案，包含視覺 Web 組件的專案項目和 Silverlight 應用程式專案項目以及這些專案項目所需的所有檔案。 專案項目範本用來將專案項目新增至現有的 SharePoint 專案，例如加入事件接收器、 站台的資料行或清單。  
  
 如需 SharePoint 的基本概念的資訊，請參閱[SharePoint Foundation 建置組塊](http://go.microsoft.com/fwlink/?LinkId=179404)。 進階的使用者可以建立自訂專案與專案項目範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
## <a name="project-templates"></a>專案範本
 以下是 SharePoint 專案範本的清單。 若要檢視中的 SharePoint 專案範本，在 Visual Studio 中，**新的專案**對話方塊方塊中，展開**SharePoint**之下的節點**Visual C#** 或**Visual Basic**，然後選擇**2010年**。  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 專案
 內容*SharePoint 2010 專案*包含在每個 SharePoint 專案範本。 SharePoint 2010 專案包含：  
  
-   專案檔。  
  
-   專案屬性 頁面中。  
  
-   A**參考**資料夾列出所有在專案中的組件參考。  
  
-   A**功能**所在的資料夾 *.feature*組態檔，用來將功能部署到 SharePoint 伺服器。  
  
-   A**封裝**所在的資料夾*封裝*用來將方案部署到 SharePoint 的檔案。  
  
-   Key.snk （強式名稱金鑰） 檔案用來簽署以強式名稱，組件的增強式安全性。  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web 組件
 *SharePoint 2010 Silverlight Web 組件*專案可讓您建立的 web 組件 for SharePoint，以便顯示 Silverlight 應用程式。 當您建立此專案時，您可以指定要新增新的 Silverlight 應用程式，它還是參考現有的帳戶。 如需詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的 web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)並[逐步解說： 建立顯示 SharePoint 之 OData 的 Silverlight web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覺 web 組件
 A *SharePoint 2010 視覺 Web 組件*專案包含*Elements.xml*定義檔**網頁組件**項目，和**使用者控制**項目. 您可以透過拖曳或複製 Visual Studio 工具箱的控制項新增至使用者控制項的介面設計視覺 web 組件的外觀。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)並[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="import-sharepoint-2010-solution-package"></a>匯入 SharePoint 2010 方案套件
 *匯入 SharePoint 2010 方案套件*專案，可讓您匯入所有或部分現有的 SharePoint 2010 網站，匯出至 SharePoint 方案 (*.wsp*) 檔案，Visual Studio。 一旦匯入到 Visual Studio，您可以自訂其項目，並重新部署它們。 如需詳細資訊，請參閱 <<c0> [ 從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>匯入可重複使用的 SharePoint 2010 工作流程
 *匯入可重複使用的 SharePoint 2010 工作流程*專案可讓您匯入到 Visual Studio 建立 SharePoint Designer 2010 中的可重複使用、 宣告式工作流程。 從 SharePoint 網站做為匯出工作流程 *.wsp*檔案。 一旦匯入到 Visual Studio，您可以進行自訂、 新增程式碼，然後將它部署至 SharePoint 網站。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。  
  
## <a name="project-item-templates"></a>專案項目範本
 以下是 SharePoint 專案項目範本的清單。 專案項目範本會將檔案新增至 SharePoint 方案，以支援 SharePoint 功能，例如站台的資料行、 清單和內容類型。 比方說，將網站資料行新增至您的解決方案將包含的網站欄專案*Elements.xml*定義檔。 新增視覺 web 組件將視覺 web 組件專案新增至您的解決方案，其中包含*Elements.xml*檔案、 使用者控制項項目和視覺 web 組件項目。  
  
 若要檢視中的 SharePoint 專案項目範本**方案總管**，開啟 SharePoint 專案的捷徑功能表，然後選擇**新增**，**新項目**。 依序展開**SharePoint**節點之下**Visual C#** 或**Visual Basic**，然後選擇**2010年**。  
  
### <a name="application-page-farm-solution-only"></a>應用程式頁面 （僅限陣列方案）
 **（僅限陣列方案） 的應用程式頁面上**項目可讓您設計[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]的 SharePoint 網站的網頁。 只能在伺服器陣列方案中可用的應用程式頁面。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)並[應用程式 _layouts 頁面類型](http://go.microsoft.com/fwlink/?LinkId=179434)。  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>商務資料連接模型 （僅限陣列方案）
 A **Business Data Connectivity 模型 （僅限陣列方案）** 項目可讓您整合商務資料至 SharePoint。 商務資料可來自後端伺服器應用程式，例如[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]、 Siebel 和服務廣告通訊協定 」 (SAP)。 商務資料連接模型只能用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)，[如何： 使用資源檔來指定當地語系化名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，和[What's New: Business Connectivity服務](http://go.microsoft.com/fwlink/?LinkId=179411)。  
  
### <a name="content-type"></a>內容類型
 *內容類型*項目可讓您建立文件、 通知、 或工作等現有的 （基底） 內容類型為基礎的自訂內容類型。 自訂內容類型會提供相同的屬性和欄位做為基底內容類型以及您定義任何站台資料行 （欄位）。 例如，您可以建立自訂的 Contact 內容類型為基礎的基底的連絡人內容類型出現在 SharePoint 中。 您可以藉由變更現有的網站欄或多個站台資料行加入已包含在基底內容類型的自訂內容類型。  
  
> [!NOTE]  
>  由於 SharePoint 的限制，您無法建立沙箱化方案的內容類型為基礎的伺服器陣列的方案內容類型。  
  
 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)並[建置組塊： 內容型別](http://go.microsoft.com/fwlink/?LinkId=179413)。  
  
### <a name="empty-element"></a>空白項目
 *空元素*最常用於定義缺少的專案或專案項目範本，在 Visual Studio 中的 SharePoint 專案項目。 當您將空的項目加入您的專案時，節點名為 EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] 包含單一檔案也就是具名*Elements.xml。* 使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式定義中所需的項目*Elements.xml*。  
  
### <a name="event-receiver"></a>事件接收器
 *事件接收器*處理事件的 SharePoint 網站，例如項目新增至清單時，web 項目刪除時，或啟動時，工作流程中的項目。 事件接收器專案項目範本可讓您處理  
  
-   列出的事件  
  
-   清單項目事件  
  
-   列出的電子郵件事件  
  
-   Web 事件  
  
-   清單工作流程事件  
  
 建立事件接收器的專案項目**事件接收器**資料夾，並包含所有事件的事件處理常式，當您建立的專案中指定單一類別檔案**SharePoint 自訂精靈**。 事件接收器類別可以處理項目，例如檔案、 欄位、 項目、 清單、 附件、 web 組件和工作流程會新增、 更新、 刪除或移除時，在 SharePoint 網站發生的事件。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)並[建置組塊： 事件處理](http://go.microsoft.com/fwlink/?LinkId=179416)。  
  
### <a name="list"></a>清單  
 清單是可重複使用基底 SharePoint 清單定義，例如行事曆] 或 [工作清單的執行個體。 之後您可以將清單加入您的解決方案，清單設計工具可讓您將網站資料行新增至清單，並建立自訂的清單資料行。 這包括從內容類型的網站資料行。 您可以指定*檢視*針對清單中，以決定將會出現在清單中的資料行。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)並[建置組塊： 清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=179421)。  
  
### <a name="module"></a>Module  
 *模組*(不到與混淆[!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]模組) 包含您想要部署到 SharePoint 伺服器，例如影像或資訊的任何檔案。 模組專案項目包含**模組**節點。 在模組節點包含兩個專案項目範本： XML 定義檔，作為模組資訊清單，以及*sample.txt*檔案、 將預留位置檔案。 如需詳細資訊，請參閱 <<c0> [ 使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)並[模組](http://go.microsoft.com/fwlink/?LinkId=179425)。  
  
### <a name="sequential-workflow-farm-solution-only"></a>循序工作流程 （僅限陣列方案）
 A*循序工作流程*是一系列的商務邏輯步驟，直到完成最後一個步驟，依序執行。 循序工作流程用來管理涉及 SharePoint 項目，例如清單和文件的程序。 您可以建立網站層級 （全域） 工作流程或清單層級 (local) 的工作流程，而且您可以選擇是否自動或手動啟動的工作流程。 這個專案項目只用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 <<c0> [ 建立 SharePoint 工作流程解決方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流程](http://go.microsoft.com/fwlink/?LinkId=260555)，並[What's New： 工作流程改進](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="silverlight-web-part"></a>Silverlight web 組件
 *Silverlight web 組件*專案項目可讓您建立的 web 組件 for SharePoint，以便顯示 Silverlight 應用程式。 當您將這個專案項目加入您的解決方案時，您可以選擇是否要加入新的 Silverlight 應用程式，或於稍後參考現有。 如需詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的 web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)並[逐步解說： 建立顯示 SharePoint 之 OData 的 Silverlight web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="site-column"></a>網站資料行
 A*站台的資料行*也稱為*欄位*，是其中一個您可以新增至 SharePoint 專案的最基本項目。 網站資料行代表一種資料，例如電話號碼、 文字註解或縣 （市） 名稱的連絡人清單中的連絡人。 如需詳細資訊，請參閱 < [for SharePoint 中建立網站資料行、 內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)並[資料行](http://go.microsoft.com/fwlink/?LinkId=226840)。  
  
### <a name="site-definition-farm-solution-only"></a>站台定義 （僅限陣列方案）
 *網站定義*專案項目包含站台定義資料夾，其中包含下列檔案：  
  
-   預設的.aspx 網頁，作為站台預設網頁。  
  
-   *Onet.xml*定義站台元件的檔案。  
  
-   指定出現在站台定義設定 webtemp xml 檔案**範本選擇**一節**新的 SharePoint 網站**頁面。  
  
 新增網站定義之後，您可以加入程式碼和檔案引入功能。 這個專案項目只用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 <<c0> [ 建立的 SharePoint 網站定義](../sharepoint/creating-site-definitions-for-sharepoint.md)並[網站定義和組態](http://go.microsoft.com/fwlink/?LinkId=260554)。  
  
### <a name="state-machine-workflow-farm-solution-only"></a>狀態機器工作流程 （僅限陣列方案）
 A*狀態機器工作流程*是一組商務邏輯狀態、 轉換及動作。 狀態機器工作流程中的步驟不會在序列中，執行相反地，它們會觸發動作和狀態。 循序工作流程，例如狀態機器工作流程是 SharePoint 項目，例如清單和文件相關聯。 同樣地，您可以建立站台層級 （全域） 的工作流程或清單層級 （本機）。 您也可以選取是否自動或手動啟動的工作流程。 這個專案項目只用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 <<c0> [ 建立 SharePoint 工作流程解決方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流程](http://go.microsoft.com/fwlink/?LinkId=260555)，並[What's New： 工作流程改進](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="user-control-farm-solution-only"></a>使用者控制項 （僅限陣列方案）
 A*使用者控制項*是自訂、 可重複使用的控制項，您可以加入其他 ASP.NET 控制項和 SharePoint 控制項。 將使用者控制項可以加入至應用程式頁面和 web 組件，在 SharePoint 中執行。 這個專案項目只用於陣列方案。 這個專案項目只能加入伺服器陣列方案。 如需詳細資訊，請參閱 < [Web 組件或應用程式頁面建立可重複使用控制項](http://go.microsoft.com/fwlink/?LinkId=226841)。  
  
### <a name="visual-web-part"></a>視覺 web 組件
 A*視覺 web 組件*專案項目包含*Elements.xml*定義檔**網頁組件**項目，和**使用者控制**項目。 您可以透過拖曳或複製 Visual Studio 工具箱的控制項新增至使用者控制項的介面設計視覺 web 組件的外觀。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)並[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="web-part"></a>Web 組件
 A *web 組件*是一種特殊的頁面呼叫網頁組件內執行的伺服器端控制項。 它們是在 SharePoint 網站上顯示之網頁的建置組塊。 Web 組件項目會提供可讓您設計 SharePoint 網站的網頁組件的檔案。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)並[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 產品和技術](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
