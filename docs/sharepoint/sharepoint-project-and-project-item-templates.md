---
title: SharePoint 專案和專案專案範本 |Microsoft Docs
description: 查看可用的 SharePoint 專案和專案專案範本，以及其使用方式的說明。
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
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
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8482a6185f670ce1bb340ff40fe277b751a39c06
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892329"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 專案和專案專案範本
  下列各節描述可用的 SharePoint 專案和專案專案範本，以及它們的使用方式。

## <a name="project-and-project-item-templates-overview"></a>專案和專案專案範本總覽
 當您在 Visual Studio 中建立新的 SharePoint 專案時，會將 SharePoint 專案加入至方案，以及該專案類型所需的所有專案專案。 例如，如果您建立 Silverlight Web 元件專案，Visual Studio 會建立一個方案，其中包含視覺 Web 元件專案專案和 Silverlight 應用程式專案專案，以及這些專案專案所需的所有檔案。 專案專案範本可用來將專案專案加入至現有的 SharePoint 專案，例如加入事件接收器、網站資料行或清單。

 如需 SharePoint 基礎的詳細資訊，請參閱 [Sharepoint Foundation 建立區塊](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14))。 Advanced users 可以建立自訂專案和專案專案範本。 如需詳細資訊，請參閱 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

## <a name="project-templates"></a>專案範本
 以下是 SharePoint 專案範本的清單。 若要在 Visual Studio 中查看 SharePoint 專案範本，請在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **sharepoint** ] 節點，然後選擇 [ **2010**]。

### <a name="sharepoint-2010-project"></a>SharePoint 2010 專案
 *Sharepoint 2010 專案* 的內容會包含在每個 sharepoint 專案範本中。 SharePoint 2010 專案包含：

- 專案檔。

- 專案屬性頁面。

- [ **參考** ] 資料夾，列出專案中的所有元件參考。

- **功能** 資料夾，其中包含用來將功能部署至 SharePoint server 的 *功能* 設定檔。

- **封裝** 資料夾，其中包含用來將方案部署到 SharePoint 的 *封裝檔案。*

- 金鑰 .snk (強式名稱金鑰) 檔案，用來以強式名稱簽署元件，以增強安全性。

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight 網頁元件
 *Sharepoint 2010 Silverlight Web 元件* 專案可讓您建立可顯示 Silverlight 應用程式的 sharepoint 網頁元件。 當您建立此專案時，可以指定是否要將新的 Silverlight 應用程式新增至其中，或參考現有的 Silverlight 應用程式。 如需詳細資訊，請參閱 [建立 sharepoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md) 和 [逐步解說：建立可顯示 sharepoint 之 OData 的 Silverlight web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覺網頁元件
 *SharePoint 2010 視覺 Web 元件* 專案包含 *Elements.xml* 定義檔、 **Web 元件** 專案和 **使用者控制項** 專案。 您可以從 Visual Studio 工具箱將控制項拖曳或複製到使用者控制項的介面，以設計視覺 web 元件的外觀。 如需詳細資訊，請參閱 [如何：使用設計工具建立 SharePoint 網頁元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 和 [建立區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

### <a name="import-sharepoint-2010-solution-package"></a>匯入 SharePoint 2010 方案套件
 匯 *入 sharepoint 2010 方案套件* 專案可讓您將所有或部分現有的 sharepoint 2010 網站匯入，並匯出到 sharepoint 方案 (*.wsp*) 檔案，進入 Visual Studio。 匯入 Visual Studio 之後，您可以自訂其專案並重新部署。 如需詳細資訊，請參閱 [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。

### <a name="import-reusable-sharepoint-2010-workflow"></a>匯入可重複使用的 SharePoint 2010 工作流程
 匯 *入可重複使用的 sharepoint 2010 工作流程* 專案可讓您將 sharepoint Designer 2010 中建立的可重複使用宣告式工作流程匯入 Visual Studio。 工作流程會從 SharePoint 網站匯出為 *.wsp* 檔。 匯入 Visual Studio 之後，您可以自訂、加入程式碼，然後將它部署到 SharePoint 網站。 如需詳細資訊，請參閱 [逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。

## <a name="project-item-templates"></a>專案專案範本
 以下是 SharePoint 專案專案範本的清單。 專案專案範本會將檔案新增至 SharePoint 方案，以支援 SharePoint 功能，例如網站資料行、清單和內容類型。 例如，將網站資料行加入至方案時，會加入包含 *Elements.xml* 定義檔的網站資料行專案。 加入視覺網頁元件時，會將視覺 web 元件專案加入至您的方案，其中包含 *Elements.xml* 檔案、使用者控制項專案和視覺化網頁元件專案。

 若要查看 SharePoint 專案專案範本，請在 [ **方案總管** 中，開啟 SharePoint 專案的快捷方式功能表，然後選擇 [ **加入**]、[ **新增專案**]。 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010**]。

### <a name="application-page-farm-solution-only"></a>應用程式頁面 (伺服器陣列解決方案僅) 
 **只有) 專案的應用程式頁面 (伺服器陣列方案**，可讓您設計 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] SharePoint 網站的網頁。 應用程式頁面只能用在伺服器陣列方案中。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱 [如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md) 和 [應用程式 _layouts 頁面類型](/previous-versions/office/aa979604(v=office.14))。

### <a name="business-data-connectivity-model-farm-solution-only"></a>商務資料連線模型只 (伺服器陣列解決方案) 
 **商務資料連線模型 (伺服陣列方案僅)** 專案可讓您將商務資料整合到 SharePoint。 商務資料可能來自後端伺服器應用程式，例如 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] ，Siebel 和服務廣告通訊協定 (SAP) 。 商務資料連線模型只能用於伺服器陣列方案。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)、 [如何：使用資源檔來指定當地語系化的名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，以及 [新功能：商務連接服務](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))。

### <a name="content-type"></a>內容類型
 *內容類型* 專案可讓您根據現有的 (基底) 內容類型（例如檔、公告或工作）來建立自訂內容類型。 自訂內容類型會提供與基底內容類型相同的屬性和欄位，以及您所定義)  (欄位的任何網站資料行。 例如，您可以根據 SharePoint 中的基底連絡人內容類型，建立自訂的連絡人內容類型。 您可以自訂內容類型，方法是變更現有的網站資料行，或新增更多網站資料行至已包含在基底內容類型中的資料行。

> [!NOTE]
> 由於 SharePoint 的限制，您無法根據沙箱化方案內容類型建立伺服器陣列方案內容類型。

 如需詳細資訊，請參閱逐步解說：建立 SharePoint 和建立區塊的 [網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) [：內容類型](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14))。

### <a name="empty-element"></a>空白項目
 *空白元素* 最常用來定義 Visual Studio 中缺少專案或專案專案範本的 SharePoint 專案專案。 當您將空的元素加入至專案時，名為 EmptyElement [x] 的節點 (其中 [x] 是唯一的數位 \) 。 EmptyElement [x] 包含名為Elements.xml 的單一檔案 *。* 您 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 可以使用語句來定義 *Elements.xml* 中所需的元素。

### <a name="event-receiver"></a>事件接收器
 *事件接收器* 會處理 SharePoint 網站中專案的事件，例如，將專案加入至清單、刪除 Web 專案時，或工作流程啟動的時間。 事件接收器專案專案範本可讓您處理

- 列出事件

- 列出專案事件

- 列出電子郵件事件

- Web 事件

- 列出工作流程事件

  事件接收器專案專案會建立具有單一類別檔案的 **事件接收器** 資料夾，其中包含您在 [ **SharePoint 自訂嚮導]** 中建立專案時所指定之所有事件的事件處理常式。 當新增、更新、刪除或移除專案（例如檔案、欄位、專案、清單、附件、網頁元件和工作流程）時，事件接收器類別可以處理在 SharePoint 網站上發生的事件。 如需詳細資訊，請參閱 [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md) 和 [建立區塊：事件處理](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))。

### <a name="list"></a>List
 清單是可重複使用之基底 SharePoint 清單定義的實例，例如行事曆或工作清單。 在您的方案中加入清單之後，清單設計工具可讓您將網站資料行加入至清單，並建立自訂清單資料行。 這包括來自內容類型的網站資料行。 您可以指定清單的 *視圖* ，以決定將出現在清單中的資料行。 如需詳細資訊，請參閱逐步解說：建立 SharePoint 和建立區塊的 [網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) [：清單和文件庫](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))。

### <a name="module"></a>模組
 *模組* (不會與模組混淆 [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]) 包含任何您想要部署到 SharePoint 伺服器的檔案，例如影像或附注。 模組專案專案包含 **模組** 節點。 模組節點包含兩個專案專案範本： XML 定義檔，可作為模組的資訊清單，以及 *sample.txt* 檔案（預留位置檔案）。 如需詳細資訊，請參閱 [使用模組來包含方案](../sharepoint/using-modules-to-include-files-in-the-solution.md) 和 [模組](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14))中的檔案。

### <a name="sequential-workflow-farm-solution-only"></a>僅限順序的工作流程 (伺服器陣列解決方案) 
 *連續工作流程* 是一連串的商務邏輯步驟，會依序執行，直到最後一個步驟完成為止。 順序工作流程是用來管理牽涉到 SharePoint 專案的進程，例如清單和檔。 您可以建立網站層級 (全域) 工作流程或清單層級 (本機) 工作流程，而且您可以選取工作流程是要自動或手動啟動。 這個專案專案只能用在伺服器陣列方案中。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱 [建立 sharepoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [sharepoint Server 2010 中的工作](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))流程，以及 [新功能：工作流程改進](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))。

### <a name="silverlight-web-part"></a>Silverlight 網頁元件
 *Silverlight web 元件* 專案專案可讓您建立可顯示 Silverlight 應用程式的 SharePoint 網頁元件。 當您將此專案專案加入至方案時，您可以選擇是否要加入新的 Silverlight 應用程式，或稍後參考現有的應用程式。 如需詳細資訊，請參閱 [建立 sharepoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md) 和 [逐步解說：建立可顯示 sharepoint 之 OData 的 Silverlight web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。

### <a name="site-column"></a>網站資料行
 *網站資料行*（也稱為 *欄位*）是您可以新增至 SharePoint 專案的最基本元素之一。 網站資料行代表一種資料類型，例如電話號碼、文字批註，或是連絡人清單中連絡人的城市名稱。 如需詳細資訊，請參閱 [建立網站資料行、內容類型，以及 SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) 和資料 [行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))的清單。

### <a name="site-definition-farm-solution-only"></a>僅) 的網站定義 (的伺服器陣列解決方案
 *網站定義* 專案專案包含網站定義資料夾，其中包含下列檔案：

- 預設的 .aspx 網頁，用來做為網站的預設網頁。

- 定義網站元件的 *onet.xml* 檔案。

- Webtemp xml 檔案，指定出現在 [**新增 SharePoint 網站**] 頁面之 **範本選擇** 區段中的網站定義設定。

  新增網站定義之後，您可以新增程式碼和檔案來引入功能。 這個專案專案只能用在伺服器陣列方案中。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱 [建立 SharePoint 的網站定義](../sharepoint/creating-site-definitions-for-sharepoint.md) 和 [網站定義和](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))設定。

### <a name="state-machine-workflow-farm-solution-only"></a>狀態機器工作流程 (伺服器陣列解決方案僅) 
 *狀態機器工作流程* 是一組商務邏輯狀態、轉換和動作。 狀態機器工作流程中的步驟不會依序執行;相反地，它們是由動作和狀態所觸發。 如同連續的工作流程，狀態機器工作流程與 SharePoint 專案相關聯，例如清單和檔。 同樣地，您可以建立網站層級 (全域) 工作流程或清單層級 (本機) 工作流程。 您也可以選擇是否要自動或手動啟動工作流程。 這個專案專案只能用在伺服器陣列方案中。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱 [建立 sharepoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [sharepoint Server 2010 中的工作](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))流程，以及 [新功能：工作流程改進](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))。

### <a name="user-control-farm-solution-only"></a>僅限使用者控制項 (伺服器陣列方案) 
 *使用者控制項* 是可重複使用的自訂控制項，您可以在其中加入其他 ASP.NET 控制項和 SharePoint 控制項。 使用者控制項可以加入至在 SharePoint 中執行的應用程式頁面和 web 元件。 這個專案專案只能用在伺服器陣列方案中。 您只能將這個專案專案加入至伺服器陣列方案。 如需詳細資訊，請參閱為 [Web 組件或應用程式頁面建立可重複使用的控制項](creating-reusable-controls-for-web-parts-or-application-pages.md)。

### <a name="visual-web-part"></a>視覺網頁元件
 *視覺化網頁元件* 專案專案包含 *Elements.xml* 定義檔、 **Web 元件** 專案和 **使用者控制項** 專案。 您可以從 Visual Studio 工具箱將控制項拖曳或複製到使用者控制項的介面，以設計視覺 web 元件的外觀。 如需詳細資訊，請參閱 [如何：使用設計工具建立 SharePoint 網頁元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 和 [建立區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

### <a name="web-part"></a>Web 組件
 *Web 元件* 是伺服器端控制項，會在一種特殊類型的頁面中執行，稱為網頁元件頁面。 它們是出現在 SharePoint 網站上的頁面構成要素。 Web 元件專案提供的檔案可讓您設計 SharePoint 網站的 web 元件。 如需詳細資訊，請參閱 [如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md) 和 [組建區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 產品和技術](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
