---
title: "建立 SharePoint Web 組件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3398364f4c9e4046c3ab4670a544a96c5ac455c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-web-parts-for-sharepoint"></a>建立 SharePoint 的 Web 組件
  藉由使用 web 組件，您可以使用瀏覽器修改內容、 外觀和行為的 SharePoint 網站的頁面。 Web 組件是在網頁組件內執行的伺服器端控制項： 它們出現在 SharePoint 網站的頁面的建置組塊。 請參閱[建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkID=182097)。  
  
 您可以建立和使用範本，從 Visual Studio 偵錯 SharePoint 網站上的 web 組件。  
  
## <a name="creating-a-web-part-in-visual-studio"></a>Visual Studio 中建立的 Web 組件  
 建立 web 組件加入**Web 組件**至任何 SharePoint 專案項目。 您可以使用**Web 組件**沙箱化方案或伺服器陣列方案中的項目。  
  
 如果您想要以視覺化方式設計的 web 組件，使用設計工具中，建立**視覺 Web 組件**專案，或新增**視覺 Web 組件**至任何 SharePoint 專案項目。 您可以使用**視覺 Web 組件**僅限陣列方案中的項目。  
  
### <a name="web-part-item"></a>Web 組件項目  
 A **Web 組件**項目提供可讓您設計的 SharePoint 網站的 web 組件檔案。 當您將加入**Web 組件**項目、 Visual Studio 專案中建立資料夾，然後將數個檔案加入至資料夾。 下表描述每個檔案。  
  
|檔案|描述|  
|----------|-----------------|  
|Elements.xml|包含專案中的功能定義檔會使用來部署 web 組件的資訊。|  
|.webpart 檔案|提供 SharePoint web 組件庫中顯示網頁組件所需的資訊。|  
|程式碼檔案|包含的方法，將控制項加入至 web 組件，以及所產生 web 組件內的自訂內容。|  
  
 如需詳細資訊，請參閱[How to： 建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。  
  
### <a name="visual-web-part-item"></a>視覺 Web 組件項目  
 視覺 web 組件是您在 Visual Studio 中使用 Visual Web Developer 設計工具建立的 web 組件。 視覺 web 組件的功能與任何其他 web 組件相同。 若要加入控制項，例如按鈕和文字方塊中的網頁組件，您可以加入程式碼為 XML 檔案。 不過，您將控制項加入視覺 web 組件拖曳，或將它們複製到 web 組件從 Visual Studio**工具箱**。 設計工具然後將必要的程式碼會產生 XML 檔案中。 請參閱[How to： 使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
## <a name="sharepoint-controls"></a>SharePoint 控制項  
 Visual Studio 會提供一些控制項，用於建立 SharePoint 頁面，例如應用程式頁面。 會出現在這些控制項**工具箱**下**SharePoint 控制項**。 這些控制項的功能是衍生自[Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315)命名空間，其中包含在 SharePoint 網站和清單頁面所使用的 ASP.NET 伺服器控制項。  
  
|控制項名稱|描述|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|插入 ASP 功能表。 如需詳細資訊，請參閱[功能表控制項概觀](http://go.microsoft.com/fwlink/?LinkId=235316)。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|插入**連結**.aspx 頁面項目，並套用所定義的一個或多個外部樣式表**CssRegistration**。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|將 DateTime 控制項插入至.aspx 網頁。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|插入的.aspx 頁面上的安全性驗證|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|傳回指定清單的屬性。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|傳回目前網站的全域屬性。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|插入 rss 摘要的.aspx 頁面連結。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|提供屬性和方法，以註冊資源，例如指令碼，在頁面上，以便它們可以呈現網頁時要求。|  
|[主題](http://go.microsoft.com/fwlink/?LinkId=235314)|佈景主題套用至.aspx 網頁。|  
  
## <a name="debugging-a-web-part"></a>偵錯的 Web 組件  
 您可以偵錯 SharePoint 專案就像您會偵錯其他 Visual Studio 專案包含 web 組件。 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。  
  
 若要偵錯程式碼開始，將 web 組件在 SharePoint web 組件頁面。  
  
 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="visual-web-part-limitations"></a>視覺 Web 組件限制  
 在 Visual Studio 中啟動，您可以將視覺 web 組件加入沙箱化 SharePoint 方案與伺服器陣列方案。 不過，視覺 web 組件具有下列限制：  
  
-   視覺 web 組件不支援可置換的參數。 如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
-   使用者控制項或視覺 web 組件無法拖曳和卸除或複製到視覺 web 組件。 此動作會導致建置錯誤。  
  
-   視覺 web 組件未直接支援 SharePoint server token，例如 $SPUrl。 如需詳細資訊，請參閱 <"語彙基元限制在沙箱化視覺 Web 組件 」 主題中[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
-   沙箱化方案中的視覺 web 組件偶爾會得到錯誤，「 沙箱化程式碼執行的要求已拒絕，因為沙箱化的程式碼主機服務已太忙碌而無法處理要求。 」 如需有關此錯誤的詳細資訊，請參閱這篇文章中的[SharePoint 開發人員團隊部落格](http://go.microsoft.com/fwlink/?LinkId=225932)。  
  
-   在 Visual Studio 中，不支援伺服器端 JavaScript 偵錯，但用戶端 JavaScript 偵錯支援。  
  
     雖然您可以將內嵌 JavaScript 加入伺服器端標記檔案，不支援偵錯中斷點加入至標記。 若要偵錯 JavaScript，參考外部 JavaScript 檔案在標記檔案中，然後 JavaScript 檔案中設定中斷點。  
  
-   偵錯內嵌的[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]必須完成程式碼，而不是標記檔案中產生的程式碼檔案中。  
  
-   視覺 web 組件不支援使用`<@ Assembly Src=`指示詞。  
  
-   SharePoint web 控制項和一些[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]控制項不支援 SharePoint sandboxed 環境中。 如果使用不支援的控制項上的視覺 web 組件，在沙箱化方案中，錯誤會出現"的類型或命名空間名稱 'Theme' 不存在於命名空間 'Microsoft.SharePoint.WebControls' 」。  
  
 如需有關沙箱化方案的詳細資訊，請參閱[沙箱之間的差異與伺服器陣列方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="creating-older-style-sharepoint-based-web-parts"></a>建立舊版樣式 Sharepoint Web 組件  
 您可以在 Visual Studio 中使用範本來建立自訂[!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]for SharePoint web 組件。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]web 組件最上層的內建[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]web 組件基礎結構，並會建議針對新的專案類型。  
  
 在極少數的情況下，您可能必須使用 sharepoint web 組件的舊樣式建立的 web 組件。 您可以使用 Visual Studio 來建立這些類型的 web 組件，但 Visual Studio 不提供任何專門設計來協助您建立的範本。  
  
 如需您可能想要建立 sharepoint web 組件的舊樣式的詳細資訊，請參閱[Web 組件基礎結構，在 Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290)。 如需如何建立使用 sharepoint web 組件的舊樣式的 web 組件的詳細資訊，請參閱[建立基本的 SharePoint Web 組件的逐步解說](http://go.microsoft.com/fwlink/?LinkId=169288)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|示範如何建立網頁組件的 SharePoint 頁面。|  
|[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|示範如何使用視覺化設計介面建立 SharePoint web 組件。|  
|[如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何建立可由應用程式頁面和 web 組件，在 SharePoint 中執行的自訂、 可重複使用控制項。|  
|[逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|描述如何設計 for SharePoint web 組件。|  
|[逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|描述如何設計 for SharePoint 的 web 組件，將控制項拖曳到視覺化設計介面。|  
|[逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何設計裝載 Silverlight 應用程式，並顯示來自 SharePoint 清單資料的 sharepoint web 組件。|  
  
  