---
title: 共用點項目和項目項目範本 |微軟文件
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649231"
---
# <a name="sharepoint-project-and-project-item-templates"></a>共用點項目與專案項目範本
  以下各節介紹可用的 SharePoint 專案和專案專案範本及其使用方式。

## <a name="project-and-project-item-templates-overview"></a>專案和專案項目樣本概述
 在 Visual Studio 中建立新的 SharePoint 專案時,SharePoint 專案將與該專案類型所需的所有專案項一起添加到解決方案中。 例如,如果創建 Silverlight Web 部件專案,Visual Studio 將建立一個解決方案,其中包含 Visual Web 部件專案項和 Silverlight 應用程式專案項以及這些專案專案所需的所有檔。 專案項範本用於將專案項添加到現有 SharePoint 專案,例如添加事件接收方、網站列或清單。

 有關 SharePoint 基礎知識的資訊,請參閱[SharePoint 基礎建構基塊](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14))。 高級用戶可以創建自定義專案和專案項範本。 有關詳細資訊,請參閱擴展[SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。

## <a name="project-templates"></a>專案範本
 以下是 SharePoint 專案範本的清單。 要查看 Visual Studio 中的 SharePoint 專案樣本,請在新**專案**對話框中展開**Visual C#** 或 Visual **Basic**下的**SharePoint**節點,然後選擇**2010**。

### <a name="sharepoint-2010-project"></a>SharePoint 2010 專案
 *SharePoint 2010 項目*的內容包含在每個 SharePoint 專案範本中。 A SharePoint 2010 專案包含:

- 項目檔。

- 項目屬性頁。

- 列出項目中所有程式集引用的**引用**資料夾。

- 包含 *.功能*配置檔**的功能**資料夾,用於將功能部署到 SharePoint 伺服器。

- 包含*包.包*檔的**包**資料夾,用於將解決方案部署到 SharePoint。

- 用於使用強名稱對程式集進行簽名的 key.snk(強名鍵)檔,以提高安全性。

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 銀光網路部分
 *SharePoint 2010 銀光 Web 部件*專案使您能夠為 SharePoint 創建顯示銀光應用程式的 Web 部件。 創建此專案時,可以指定是向它添加新 Silverlight 應用程式還是引用現有應用程式。 有關詳細資訊,請參閱為[SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)和演練建立 Web 組件[:建立顯示共享點的 OData 的銀光 Web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。

### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覺化 Web 組件
 *SharePoint 2010 可視化 Web 部件*專案包括*元素.xml*定義檔 **、Web 部件**項和**使用者控制**項。 您可以通過將控制式裝置從 Visual Studio 工具箱拖動或複製到使用者控制式外觀的表面來設計可視 Web 元件的外觀。 有關詳細資訊,請參閱[如何:使用設計器](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和建構基塊創建 SharePoint Web[元件:Web 部件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

### <a name="import-sharepoint-2010-solution-package"></a>匯入 SharePoint 2010 解決方案套件
 *導入 SharePoint 2010 解決方案套件*專案允許您將現有 SharePoint 2010 網站的全部或部分(匯出到 SharePoint 解決方案 *(.wsp*) 檔)導入 Visual Studio。 導入 Visual Studio 後,可以自定義其專案並重新部署它們。 有關詳細資訊,請參閱[從現有 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。

### <a name="import-reusable-sharepoint-2010-workflow"></a>匯入可重用的 SharePoint 2010 工作流
 *導入可重用 SharePoint 2010 工作流*專案,允許您將在 SharePoint 設計器 2010 中創建的可重用聲明性工作流導入 Visual Studio。 工作流從 SharePoint 網站匯出為 *.wsp*檔。 導入 Visual Studio 後,可以對其進行自定義、向其添加代碼,然後將其部署到 SharePoint 網站。 有關詳細資訊,請參閱[演練:將 SharePoint 設計器可重用工作流導入可視化工作室](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。

## <a name="project-item-templates"></a>專案專案範本
 以下是 SharePoint 專案範本的清單。 專案專案範本將檔添加到 SharePoint 解決方案,以支援 SharePoint 功能(如網站列、清單和內容類型)。 例如,向解決方案添加網站列會添加包含*Elements.xml*定義檔的網站列專案。 添加可視 Web 部件會將可視 Web 部件專案添加到包含*Elements.xml*檔案、使用者控制項項和可視 Web 部件項的解決方案中。

 要查看 SharePoint 專案範本,在**解決方案資源管理器**中,打開 SharePoint 專案的快捷功能表,然後選擇 **「添加****」「新專案**」。 在**Visual C#** 或**視覺化基本**項目下展開**SharePoint**節點,然後選擇**2010**。

### <a name="application-page-farm-solution-only"></a>應用程式頁(僅限伺服器場解決方案)
 應用程式**頁(僅限伺服器場解決方案)** 專案使您能夠為[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]SharePoint 網站設計網頁。 應用程式頁只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱[如何:建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)和[應用程式_layouts頁面類型](/previous-versions/office/aa979604(v=office.14))。

### <a name="business-data-connectivity-model-farm-solution-only"></a>商務資料連線模型(僅限伺服器場解決方案)
 **業務數據連接模型(僅限伺服器場解決方案)** 專案使您能夠將業務數據集成到 SharePoint 中。 業務數據可能來自後端伺服器應用程式,如[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]Siebel 和服務廣告協定 (SAP)。 業務數據連接模型只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱[:建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md),[如何:使用資源檔指定本地化名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md),以及[新增內容:業務連接服務](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))。

### <a name="content-type"></a>內容類型
 *內容類型*專案允許您基於現有(基本)內容類型(如文檔、公告或任務)創建自定義內容類型。 自定義內容類型提供與基本內容類型相同的屬性和欄位以及定義的任何網站列(欄位)。 例如,您可以創建基於 SharePoint 中的基本連絡人內容類型的自定義連絡人內容類型。 您可以通過更改現有網站列或將更多網站列添加到基本內容類型中已包含的網站列來自定義內容類型。

> [!NOTE]
> 由於 SharePoint 限制,您不能基於沙箱解決方案內容類型創建伺服器場解決方案內容類型。

 有關詳細資訊,請參閱演練:為 SharePoint 和[建構基塊:內容類型](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14))[創建網站列、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。

### <a name="empty-element"></a>空白項目
 *空元素*最常用於定義 Visual Studio 中缺少專案或專案項範本的 SharePoint 專案項。 向專案添加空元素時,將創建名為 emptyElement_x_(其中 [x] 是唯\)一編號 的節點。 空元素[x] 包含名為*Element.xml*的單個檔。 使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]語句在*Elements.xml*中定義所需的元素。

### <a name="event-receiver"></a>事件接收器
 *事件接收方*處理 SharePoint 網站中專案的事件,例如將專案添加到清單中時、刪除 Web 項時或工作流啟動時間。 事件接收器項目項目樣本允許您處理

- 列出事件

- 列出項目事件

- 列出電子郵件事件

- Web 事件

- 列出工作流事件

  事件接收器項目項創建一個**事件接收器**資料夾,其中包含單個類檔,其中包含您在**SharePoint 自定義嚮導**中創建專案時指定的所有事件的事件處理程式。 事件接收者類可以處理在添加、更新、刪除或刪除檔、欄位、專案、清單、附件、Web 部件和工作流等專案時在 SharePoint 網站上發生的事件。 有關詳細資訊,請參閱[如何:建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)和[建構基塊:事件處理](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))。

### <a name="list"></a>清單
 清單是可重用的基本 SharePoint 列表定義的實例,如日曆或任務清單。 將清單新增到解決方案後,清單設計器使您能夠將網站列添加到清單中並創建自訂清單列。 這包括內容類型的網站列。 您可以為清單指定*檢視*,該檢視確定將顯示在清單中的欄位。 有關詳細資訊,請參閱演練:為 SharePoint 和[建構基塊:清單和文件庫](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14))[創建網站列、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。

### <a name="module"></a>模組
 *模組*(不要[!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]與 模組混淆)包含要部署到 SharePoint 伺服器的任何檔,如圖像或註釋。 模組專案項包含**模組**節點。 模組節點包含兩個項目項範本:一個 XML 定義檔(充當模組的清單)和一個*樣板.txt*檔(占位元檔)。 有關詳細資訊,請參閱[Modules](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14))[使用模組在解決方案和模組中包含檔](../sharepoint/using-modules-to-include-files-in-the-solution.md)。

### <a name="sequential-workflow-farm-solution-only"></a>循序工作流(僅限伺服器場解決方案)
 *順序工作流*是一系列業務邏輯步驟,按順序執行,直到最後一步完成。 順序工作流用於管理涉及 SharePoint 項(如清單和文檔)的進程。 您可以創建網站級(全域)工作流或清單級(本地)工作流,也可以選擇工作流是自動啟動還是手動啟動。 此專案項只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱創建[SharePoint 工作流解決方案](../sharepoint/creating-sharepoint-workflow-solutions.md)[、SharePoint 伺服器 2010 中的工作流](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))以及[新增功能:工作流改進](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))。

### <a name="silverlight-web-part"></a>銀光網部分
 *Silverlight Web 部件*專案專案專案使您能夠為 SharePoint 創建顯示銀光應用程式的 Web 部件。 將此專案項添加到解決方案時,可以選擇是添加新 Silverlight 應用程式還是稍後引用現有應用程式。 有關詳細資訊,請參閱為[SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)和演練建立 Web 組件[:建立顯示共享點的 OData 的銀光 Web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。

### <a name="site-column"></a>網站列
 *網站列*(也稱為*欄位*)是可以添加到 SharePoint 專案的最基本元素之一。 網站列表示數據類型,如電話號碼、文本註釋或聯繫人清單中連絡人的城市名稱。 有關詳細資訊,請參閱為[SharePoint 和列建立網站列、內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)。 [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

### <a name="site-definition-farm-solution-only"></a>站台定義 (僅限伺服器場解決方案)
 *網站定義*項目項目包含一個網站定義資料夾,其中包含以下檔案:

- 預設 .aspx 頁,用作網站的默認網頁。

- 定義網站元件的*onet.xml*檔案。

- 一個 Webtemp xml 檔,用於指定在新**SharePoint 網站**頁面的 **「範本選擇**」部分中顯示的站點定義配置。

  新增網站定義後,添加代碼和檔以引入功能。 此專案項只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱為[SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)和[網站定義和配置](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))創建網站定義。

### <a name="state-machine-workflow-farm-solution-only"></a>狀態機工作流(僅限伺服器場解決方案)
 *狀態機工作流*是一組業務邏輯狀態、轉換和操作。 狀態機工作流中的步驟不按順序執行;因此,這些步驟不會按順序執行。相反,它們由操作和狀態觸發。 與順序工作流一樣,狀態機工作流與 SharePoint 項(如清單和文檔)相關聯。 同樣,您可以創建網站級(全域)工作流或清單級(本地)工作流。 您還可以選擇工作流是自動啟動還是手動啟動。 此專案項只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱創建[SharePoint 工作流解決方案](../sharepoint/creating-sharepoint-workflow-solutions.md)[、SharePoint 伺服器 2010 中的工作流](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))以及[新增功能:工作流改進](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))。

### <a name="user-control-farm-solution-only"></a>使用者控制 (僅限伺服器場解決方案)
 *使用者控制項*是自訂的、可重用的控制項,您可以將其他ASP.NET控制項和SharePoint控制項添加到其中。 可以將使用者控制件添加到在 SharePoint 中執行的應用程式頁和 Web 部件中。 此專案項只能在伺服器場解決方案中使用。 只能將此專案項添加到伺服器場解決方案。 有關詳細資訊,請參閱為[Web 元件或應用程式頁建立可重用控制件](creating-reusable-controls-for-web-parts-or-application-pages.md)。

### <a name="visual-web-part"></a>視覺網頁元件
 *可視 Web 部件*專案項目包括*Elements.xml*定義檔 **、Web 部件**項和**使用者控制**項。 您可以通過將控制式裝置從 Visual Studio 工具箱拖動或複製到使用者控制式外觀的表面來設計可視 Web 元件的外觀。 有關詳細資訊,請參閱[如何:使用設計器](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和建構基塊創建 SharePoint Web[元件:Web 部件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

### <a name="web-part"></a>Web 組件
 *Web 部件*是伺服器端控制項,在稱為 Web 部件頁的特殊類型的頁面內執行。 它們是顯示在 SharePoint 網站上的頁面建構基塊。 Web 部件項提供檔,使您能夠為 SharePoint 網站設計 Web 部件。 有關詳細資訊,請參閱[如何:創建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)和[建構基塊:Web 部件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 產品和技術](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
