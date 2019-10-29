---
title: 建立 SharePoint 的 Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82e0d860f21f0fe2744c8c05c4ebeb3590be68fc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984470"
---
# <a name="create-web-parts-for-sharepoint"></a>建立 SharePoint 的 web 元件
  藉由使用 web 元件，您可以使用瀏覽器來修改 SharePoint 網站頁面的內容、外觀和行為。 Web 元件是在 web 元件頁面內執行的伺服器端控制項：它們是出現在 SharePoint 網站上的頁面建立區塊。 請參閱[建立區塊： Web 組件](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))。

 您可以使用 Visual Studio 的範本，在 SharePoint 網站上建立和偵錯工具 web 元件。

## <a name="create-a-web-part-in-visual-studio"></a>在 Visual Studio 中建立 web 元件
 藉由將**Web 元件**專案新增至任何 SharePoint 專案來建立 web 元件。 您可以在沙箱化方案或伺服器陣列方案中使用**Web 元件**專案。

 如果您想要使用設計工具以視覺化方式設計 web 元件，請建立**視覺 Web 元件**專案，或將**視覺 web 元件**專案加入至任何 SharePoint 專案。 您只能在伺服器陣列方案中使用**視覺 Web 元件**專案。

### <a name="web-part-item"></a>Web 元件專案
 **Web 元件**專案會提供檔案，讓您用來設計 SharePoint 網站的網頁元件。 當您新增**網頁元件**專案時，Visual Studio 會在專案中建立資料夾，然後將數個檔案新增至資料夾。 下表描述每個檔案。

|檔案|描述|
|----------|-----------------|
|*元素 .xml*|包含專案中的功能定義檔用來部署 web 元件的資訊。|
|webpart 檔案|提供 SharePoint 在 web 元件庫中顯示網頁元件所需的資訊。|
|程式碼檔案|包含將控制項加入 web 元件，並在 web 元件中產生自訂內容的方法。|

 如需詳細資訊，請參閱[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。

### <a name="visual-web-part-item"></a>視覺 web 元件專案
 視覺 web 元件是您在 Visual Studio 中使用 Visual Web Developer designer 建立的 web 元件。 視覺 web 元件的功能與其他任何 web 元件相同。 若要將控制項（例如按鈕和文字方塊）加入至 web 元件，請將程式碼加入至 XML 檔案。 不過，您可以從 [Visual Studio**工具箱**] 將控制項拖曳或複製到 web 元件，以將其加入至視覺 web 元件。 然後，設計工具會在 XML 檔案中產生必要的程式碼。 請參閱[如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。

## <a name="sharepoint-controls"></a>SharePoint 控制項
 Visual Studio 提供一些控制項來建立 SharePoint 頁面，例如應用程式頁面。 這些控制項會出現在 [**工具箱**] 的 [ **SharePoint 控制項**] 底下。 這些控制項的功能衍生自[WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15))命名空間，其中包含 SharePoint 網站和清單頁面上所使用的 ASP.NET 伺服器控制項。

|控制項名稱|描述|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|插入 ASP 功能表。 如需詳細資訊，請參閱[Menu 控制項總覽](/previous-versions/ecs0x9w5(v=vs.140))。|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|將**LINK**元素插入 *.aspx*頁面，並套用**CssRegistration**所定義的一或多個外部樣式表單。|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|將日期時間控制項插入 *.aspx*頁面。|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|將安全性驗證插入 *.aspx*頁面|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|傳回指定之清單的屬性。|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|傳回目前網站的全域屬性。|
|[.Rsslink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|將 RSS 摘要的連結插入 *.aspx*頁面。|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|提供屬性和方法，以便在頁面上註冊資源（例如腳本），以便在呈現頁面時要求它們。|
|[主題](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|將主題套用至 *.aspx*頁面。|

## <a name="debug-a-web-part"></a>Debug web 元件
 您可以將包含 web 元件的 SharePoint 專案，如同您在進行其他 Visual Studio 專案的偵錯工具一樣進行 debug。 當您啟動 [Visual Studio 偵錯工具] 時，Visual Studio 會開啟 SharePoint 網站。

 若要開始偵錯工具代碼，請將 web 元件加入至 SharePoint 中的 web 元件頁面。

 如需如何對 SharePoint 專案進行偵錯工具的詳細資訊，請參閱針對[sharepoint 方案進行疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。

## <a name="visual-web-part-limitations"></a>視覺 web 元件限制
 從 Visual Studio 開始，您可以將視覺 web 元件加入至沙箱化 SharePoint 方案和伺服器陣列方案。 不過，visual web part 的限制如下：

- 視覺 web 元件不支援可取代的參數。 如需詳細資訊，請參閱可[取代的參數](../sharepoint/replaceable-parameters.md)。

- 使用者控制項或視覺 web 元件無法拖放或複製到視覺 web 元件上。 此動作會導致建立錯誤。

- 視覺 web 元件不直接支援 SharePoint 伺服器權杖，例如 $SPUrl。 如需詳細資訊，請參閱針對[SharePoint 方案進行疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)主題中的

- 沙箱化方案中的視覺 web 元件偶爾會收到錯誤：「因為沙箱化程式碼主機服務過於忙碌而無法處理要求，所以已拒絕沙箱化程式碼執行要求。」 如需有關此錯誤的詳細資訊，請參閱[SharePoint 開發人員小組 Blog](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157)中的這篇文章。

- Visual Studio 不支援伺服器端的 JavaScript 調試，但是支援用戶端 JavaScript 調試。

   雖然您可以將內嵌 JavaScript 新增至伺服器端標記檔案，但不支援對加入至標記的中斷點進行偵錯工具。 若要進行 JavaScript 的偵錯工具，請參考標記檔案中的外部 JavaScript 檔案，然後在 JavaScript 檔案中設定中斷點。

- 內嵌 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 程式碼的偵錯工具必須在產生的程式碼檔案中完成，而不是在標記檔案中進行。

- 視覺 web 元件不支援使用 `<@ Assembly Src=` 指示詞。

- Sharepoint 沙箱環境不支援 SharePoint web 控制項和部分 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 控制項。 如果在沙箱化方案中的視覺 web 元件上使用不支援的控制項，則會出現錯誤：「類型或命名空間名稱 ' 主題 ' 不存在於命名空間 ' WebControls '」中。

  如需沙箱化方案的詳細資訊，請參閱[沙箱與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。

## <a name="create-older-style-sharepoint-based-web-parts"></a>建立以 SharePoint 為基礎的舊版 web 元件
 您可以使用 Visual Studio 中的範本來建立 SharePoint 的自訂 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web 元件。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web 元件是建置於 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] web 元件基礎結構之上，而且是新專案的建議類型。

 在極少數的情況下，您可能必須使用舊版的 SharePoint web 元件來建立 web 元件。 您可以使用 Visual Studio 來建立這些類型的 web 元件，但是 Visual Studio 不會提供專為協助您建立而設計的範本。

 如需有關何時可能要建立舊版 SharePoint web 元件的詳細資訊，請參閱[Windows Sharepoint Services 中的 Web 元件基礎結構](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14))。 如需如何使用舊版以 SharePoint 為基礎的 web 元件來建立 web 元件的詳細資訊，請參閱[逐步解說建立基本的 Sharepoint Web 元件](/previous-versions/office/ms452873(v=office.14))。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|說明如何建立 SharePoint 網頁的 web 元件。|
|[如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|示範如何使用視覺化設計介面來建立 SharePoint 的 web 元件。|
|[如何：為 SharePoint 應用程式頁面或 web 元件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何建立可重複使用的自訂控制項，以供在 SharePoint 中執行的應用程式頁面和 web 元件使用。|
|[逐步解說：建立 SharePoint 的 web 元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|說明如何設計 SharePoint 的網頁元件。|
|[逐步解說：使用設計工具建立 SharePoint 的 web 元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|描述如何藉由將控制項拖曳至視覺化設計介面，設計 SharePoint 的 web 元件。|
|[逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight web 元件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何設計主控 Silverlight 應用程式的 SharePoint web 元件，並顯示來自 SharePoint 清單的資料。|
