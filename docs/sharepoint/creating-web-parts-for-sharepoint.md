---
title: 建立 SharePoint Web 組件 |Microsoft Docs
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
ms.openlocfilehash: 1105e6c68e1ec9083fd790ad8a38b09870345af2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580940"
---
# <a name="create-web-parts-for-sharepoint"></a>建立 SharePoint web 組件
  藉由使用 web 組件，您可以使用瀏覽器修改內容、 外觀及行為的 SharePoint 網站頁面。 Web 組件是在網頁組件內執行的伺服器端控制項： 它們是在 SharePoint 網站上顯示之網頁的建置組塊。 請參閱[建置組塊：Web 組件](http://go.microsoft.com/fwlink/?LinkID=182097)。

 您可以建立並使用範本從 Visual Studio 偵錯 SharePoint 網站上的 web 組件。

## <a name="create-a-web-part-in-visual-studio"></a>在 Visual Studio 中建立的 web 組件
 建立 web 組件，藉由新增**Web 組件**至任何 SharePoint 專案項目。 您可以使用**Web 組件**沙箱化方案或伺服陣列方案中的項目。

 如果您想要使用設計工具以視覺化方式設計 web 組件，建立**視覺化網頁組件**專案，或新增**視覺 Web 組件**至任何 SharePoint 專案項目。 您可以使用**視覺化網頁組件**僅限陣列方案中的項目。

### <a name="web-part-item"></a>Web 組件項目
 A **Web 組件**項目可提供您可用來設計 SharePoint 網站的網頁組件的檔案。 當您將加入**Web 組件**項目時，Visual Studio 在您的專案中建立資料夾，然後將數個檔案加入資料夾。 下表描述每個檔案。

|檔案|描述|
|----------|-----------------|
|*Elements.xml*|包含在專案中的功能定義檔案用來部署 web 組件資訊。|
|.webpart 檔|提供 SharePoint web 組件庫中顯示您的 web 組件所需的資訊。|
|程式碼檔案|包含的方法，將控制項加入至網頁組件，並可產生網頁組件內的自訂內容。|

 如需詳細資訊，請參閱[如何：建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。

### <a name="visual-web-part-item"></a>視覺 web 組件項目
 視覺 web 組件是您在 Visual Studio 中使用 Visual Web Developer 設計工具建立的 web 組件。 視覺 web 組件的功能與任何其他 web 組件相同。 若要加入的 web 組件控制項，例如按鈕和文字方塊中，您可以加入程式碼至 XML 檔案。 不過，您將控制項加入至視覺 web 組件拖曳，或將它們複製到 web 組件中，從 Visual Studio**工具箱**。 設計工具接著會產生 XML 檔案中的所需的程式碼。 請參閱[如何：使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。

## <a name="sharepoint-controls"></a>SharePoint 控制項
 Visual Studio 會提供一些控制項，用於建立 SharePoint 頁面，例如應用程式頁面。 這些控制項會出現在**工具箱**下方**SharePoint 控制項**。 這些控制項的功能衍生自[Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315)命名空間，其中包含 SharePoint 網站和清單頁面所使用的 ASP.NET 伺服器控制項。

|控制項名稱|描述|
|------------------|-----------------|
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|插入 ASP 功能表。 如需詳細資訊，請參閱 < [ 功能表控制項概觀](http://go.microsoft.com/fwlink/?LinkId=235316)。|
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|插入**連結**項目 *.aspx*頁面上，並套用所定義的一或多個外部樣式表**CssRegistration**。|
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|插入將 DateTime 控制項插入 *.aspx*頁面。|
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|將安全性驗證到 *.aspx*頁面|
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|傳回指定清單的屬性。|
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|傳回目前網站的全域屬性。|
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|插入連結 RSS 摘要 *.aspx*頁面。|
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|提供屬性和方法，以註冊資源，例如指令碼，在頁面上，以便它們可以在呈現網頁要求。|
|[主題](http://go.microsoft.com/fwlink/?LinkId=235314)|若要將佈景主題套用 *.aspx*頁面。|

## <a name="debug-a-web-part"></a>偵錯的 web 組件
 您可以偵錯 SharePoint 專案，其中包含 web 組件，就如同您會偵錯其他 Visual Studio 專案。 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。

 若要開始偵錯程式碼，請先在 SharePoint 中的網頁組件頁面中加入 web 組件。

 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

## <a name="visual-web-part-limitations"></a>視覺 web 組件限制
 開始在 Visual Studio 中，您可以將視覺 web 組件新增至沙箱化 SharePoint 方案與伺服器陣列方案。 不過，視覺 web 組件具有下列限制：

- 視覺 web 組件不支援可置換的參數。 如需詳細資訊，請參閱 <<c0> [ 可置換的參數](../sharepoint/replaceable-parameters.md)。

- 使用者控制項或視覺 web 組件無法拖曳和卸除或複製到視覺 web 組件。 這個動作會導致建置錯誤。

- 視覺 web 組件不直接支援 SharePoint 伺服器語彙基元，例如 $SPUrl。 詳細的資訊，請參閱主題中的 「 權杖限制在沙箱化視覺 Web 組件 」[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

- 在沙箱化方案中的視覺 web 組件偶而會收到錯誤訊息、 「"沙箱化程式碼執行要求被拒絕的沙箱化程式碼主機服務太忙碌，無法處理要求，因為。 如需此錯誤的詳細資訊，請參閱在這篇文章[SharePoint 開發人員小組部落格](http://go.microsoft.com/fwlink/?LinkId=225932)。

- 伺服器端 JavaScript 偵錯不支援在 Visual Studio 中，但用戶端 JavaScript 偵錯支援。

   雖然您可以將內嵌 JavaScript 加入到伺服器端標記檔案中，偵錯不支援為加入至標記的中斷點。 若要偵錯 JavaScript，參考在標記檔案中的外部 JavaScript 檔案，然後在 JavaScript 檔案中設定中斷點。

- 內嵌的偵錯[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]中產生的程式碼檔案而不是標記檔案中，必須完成的程式碼。

- 視覺 web 組件不支援使用`<@ Assembly Src=`指示詞。

- SharePoint web 控制項和部分[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]控制項不支援在 SharePoint 的沙箱環境中。 如果使用不支援的控制項上的視覺 web 組件，在沙箱化方案中，錯誤會出現"的類型或命名空間名稱 'Theme' 不存在於命名空間 'Microsoft.SharePoint.WebControls' 」。

  如需有關沙箱化方案的詳細資訊，請參閱[差異沙箱化方案與伺服器陣列解決方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。

## <a name="create-older-style-sharepoint-based-web-parts"></a>建立舊樣式 SharePoint 架構 web 組件
 您可以在 Visual Studio 中使用範本來建立自訂[!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]適用於 SharePoint web 組件。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web 組件為基礎建置的[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]web 組件基礎結構和建議針對新的專案類型。

 在極少數的情況下，您可能使用舊樣式 SharePoint 架構 web 組件建立的 web 組件。 您可以使用 Visual Studio 來建立這些類型的 web 組件，但 Visual Studio 不提供任何設計範本，是專為協助您建立它們。

 如需有關當您可能想要建立舊樣式 SharePoint 架構 web 組件的詳細資訊，請參閱[Windows SharePoint Services 中的 Web 組件基礎結構](http://go.microsoft.com/fwlink/?LinkId=169290)。 如需如何使用舊樣式 SharePoint 架構 web 組件建立的 web 組件的詳細資訊，請參閱[逐步解說建立基本的 SharePoint Web 組件](http://go.microsoft.com/fwlink/?LinkId=169288)。

## <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[如何：建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|說明如何建立 SharePoint 頁面的 web 組件。|
|[如何：使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|說明如何使用視覺化設計介面建立 SharePoint web 組件。|
|[如何：建立 SharePoint 應用程式頁面或 web 組件的使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|說明如何建立可由應用程式頁面和 web 組件，在 SharePoint 中執行的自訂、 可重複使用的控制項。|
|[逐步解說：建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|描述如何設計 SharePoint web 組件。|
|[逐步解說：使用設計工具建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|描述如何設計適用於 SharePoint 的 web 組件，將控制項拖曳至視覺化設計介面。|
|[逐步解說：建立顯示 SharePoint 之 OData 的 Silverlight web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|描述如何設計裝載 Silverlight 應用程式，並顯示從 SharePoint 清單資料的 SharePoint web 組件。|
