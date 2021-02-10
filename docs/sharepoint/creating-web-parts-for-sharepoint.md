---
title: 建立 SharePoint 的 Web 組件 |Microsoft Docs
description: 建立 SharePoint 的網頁元件。 藉由使用網頁元件，您可以使用瀏覽器來修改 SharePoint 網站網頁的內容、外觀和行為。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae28ab44b12c979f3c405bd7d853d7a2d196aae4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948930"
---
# <a name="create-web-parts-for-sharepoint"></a>建立 SharePoint 的網頁元件
  藉由使用網頁元件，您可以使用瀏覽器來修改 SharePoint 網站網頁的內容、外觀和行為。 Web 元件是在 web 元件頁面內執行的伺服器端控制項：它們是出現在 SharePoint 網站上的網頁構成要素。 請參閱 [建立區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

 您可以使用 Visual Studio 中的範本，在 SharePoint 網站上建立和偵錯工具的網頁元件。

## <a name="create-a-web-part-in-visual-studio"></a>在 Visual Studio 中建立網頁元件
 藉由將 **Web 元件** 專案加入至任何 SharePoint 專案，建立網頁元件。 您可以使用沙箱化方案或伺服器陣列方案中的 **Web 元件** 專案。

 如果您想要使用設計工具以視覺化方式設計網頁元件，請建立 **Visual Web 元件** 專案或將 **visual web 元件** 專案加入至任何 SharePoint 專案。 您只可以在伺服器陣列方案中使用 **視覺網頁元件** 專案。

### <a name="web-part-item"></a>Web 元件專案
 **Web 元件** 專案會提供您可用來設計 SharePoint 網站網頁元件的檔案。 當您加入 **Web 元件** 專案時，Visual Studio 會在專案中建立資料夾，然後將數個檔案加入至資料夾。 下表說明每個檔案。

|檔案|描述|
|----------|-----------------|
|*Elements.xml*|包含專案中的功能定義檔用來部署網頁元件的資訊。|
|webpart 檔案|提供 SharePoint 在 web 元件庫中顯示網頁元件所需的資訊。|
|程式碼檔案|包含將控制項加入網頁元件，以及在網頁元件中產生自訂內容的方法。|

 如需詳細資訊，請參閱 [如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。

### <a name="visual-web-part-item"></a>視覺化網頁元件專案
 視覺化網頁元件是您使用 Visual Studio 中的 Visual Web Developer designer 所建立的 web 元件。 視覺化網頁元件的運作方式與任何其他網頁元件相同。 若要將控制項（例如按鈕和文字方塊）新增至網頁元件，請將程式碼加入至 XML 檔案。 不過，您可以將控制項從 Visual Studio **工具箱** 拖曳或複製到網頁元件上，藉以將控制項加入至視覺網頁元件。 然後，設計工具會在 XML 檔案中產生必要的程式碼。 請參閱 [如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。

## <a name="sharepoint-controls"></a>SharePoint 控制項
 Visual Studio 提供建立 SharePoint 頁面的一些控制項，例如應用程式頁面。 這些控制項會出現在 [ **工具箱** ] 的 **SharePoint 控制項** 底下。 這些控制項的功能衍生自 [WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) 命名空間，此命名空間包含用於 SharePoint 網站和清單頁面的 ASP.NET 伺服器控制項。

|控制項名稱|Description|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|插入 ASP 功能表。 如需詳細資訊，請參閱 [功能表控制項總覽](/previous-versions/ecs0x9w5(v=vs.140))。|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|將 **LINK** 元素插入 *.aspx* 頁面，並套用 **CssRegistration** 所定義的一或多個外部樣式表單。|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|將 DateTime 控制項插入 *.aspx* 頁面中。|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|將安全性驗證插入 *.aspx* 頁面|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|傳回指定之清單的屬性。|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|傳回目前網站的全域屬性。|
|[.Rsslink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|將 RSS 摘要的連結插入 *.aspx* 頁面中。|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|提供屬性和方法，以便在頁面上註冊資源，例如腳本，以便在轉譯頁面時要求這些資源。|
|[佈景主題](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|將主題套用至 *.aspx* 頁面。|

## <a name="debug-a-web-part"></a>調試網頁元件
 您可以對包含 web 元件的 SharePoint 專案進行 debug 錯，就像您在調試其他 Visual Studio 專案一樣。 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。

 若要開始對程式碼進行程式碼驗證，請將網頁元件新增至 SharePoint 中的 web 元件頁面。

 如需有關如何對 SharePoint 專案進行偵錯工具的詳細資訊，請參閱 [疑難排解 sharepoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

## <a name="visual-web-part-limitations"></a>視覺網頁元件限制
 從 Visual Studio 開始，您可以將視覺 web 元件加入至沙箱化 SharePoint 方案和伺服器陣列方案。 不過，視覺網頁元件有下列限制：

- 視覺 web 元件不支援可取代的參數。 如需詳細資訊，請參閱可 [取代的參數](../sharepoint/replaceable-parameters.md)。

- 使用者控制項或視覺 web 元件無法拖放或複製到視覺網頁元件。 此動作會造成組建錯誤。

- Visual web part 不直接支援 SharePoint server token，例如 $SPUrl。 如需詳細資訊，請參閱 [SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)主題中的「沙箱化視覺效果中的權杖限制 Web 組件」。

- 沙箱化方案中的視覺網頁元件偶爾會收到錯誤：「沙箱化程式碼執行要求被拒，因為沙箱化程式碼主機服務太忙碌而無法處理要求。」 如需有關此錯誤的詳細資訊，請參閱 [SharePoint 開發人員小組 Blog](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157)中的這篇文章。

- Visual Studio 中不支援伺服器端的 JavaScript 偵錯工具，但支援用戶端的 JavaScript 偵錯工具。

   雖然您可以將內嵌 JavaScript 加入至伺服器端標記檔案，但是不支援對新增至標記的中斷點進行偵錯工具。 若要 debug JavaScript，請參考標記檔案中的外部 JavaScript 檔案，然後在 JavaScript 檔案中設定中斷點。

- 內嵌程式碼的偵錯工具 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 必須在產生的程式碼檔案中執行，而不是在標記檔案中。

- 視覺 web 元件不支援使用指示詞 `<@ Assembly Src=` 。

- Sharepoint 的沙箱化環境不支援 SharePoint web 控制項和某些 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 控制項。 如果沙箱化方案中的視覺網頁元件使用不支援的控制項，則會出現「類型或命名空間名稱 ' 主題 ' 不存在於命名空間 ' WebControls '」的錯誤。

  如需沙箱化方案的詳細資訊，請參閱 [沙箱化與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。

## <a name="create-older-style-sharepoint-based-web-parts"></a>建立舊版樣式的 SharePoint 網頁元件
 您可以使用 Visual Studio 中的範本來建立 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] 適用于 SharePoint 的自訂網頁元件。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web 元件是 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 以網頁元件基礎結構為基礎，而且是新專案的建議類型。

 在極少數的情況下，您可能必須使用舊版樣式的 SharePoint 網頁元件來建立網頁元件。 您可以使用 Visual Studio 來建立這些類型的網頁元件，但 Visual Studio 不提供任何專為協助您建立的範本而設計的範本。

 如需有關何時可能想要建立舊版樣式的 SharePoint 網頁元件的詳細資訊，請參閱 [Windows Sharepoint Services 中的網頁元件基礎結構](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14))。 如需如何使用舊版樣式的 SharePoint 網頁元件建立網頁元件的詳細資訊，請參閱 [建立基本 Sharepoint 網頁元件的逐步](/previous-versions/office/ms452873(v=office.14))解說。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|說明如何建立 SharePoint 網頁的 web 元件。|
|[如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|說明如何使用視覺化設計介面建立 SharePoint 的網頁元件。|
|[如何：為 SharePoint 應用程式頁面或 web 元件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何建立可供在 SharePoint 中執行的應用程式頁面和 web 元件使用的自訂、可重複使用的控制項。|
|[逐步解說：建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|描述如何設計 SharePoint 的網頁元件。|
|[逐步解說：使用設計工具建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|描述如何將控制項拖曳至視覺化設計介面，以設計 SharePoint 的 web 元件。|
|[逐步解說：建立顯示適用于 SharePoint 之 OData 的 Silverlight web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何設計 SharePoint 的 web 元件，以裝載 Silverlight 應用程式並顯示來自 SharePoint 清單的資料。|