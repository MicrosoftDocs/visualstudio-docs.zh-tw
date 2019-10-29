---
title: 建立 SharePoint 的應用程式頁面 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47f403f4eec6ec66563ae88bec226e073f625716
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981104"
---
# <a name="create-application-pages-for-sharepoint"></a>建立 SharePoint 的應用程式頁面
  *應用程式頁面*是針對在 SharePoint 網站中使用而設計的 ASP.NET 網頁。 應用程式頁面是特殊類型的 ASP.NET 網頁。 應用程式頁面和標準 ASP.NET 網頁之間的主要差異在於，應用程式頁面包含與 SharePoint 主版頁面合併的內容。 主版頁面可讓應用程式頁面與網站上的其他頁面共用相同的外觀和行為。

 Visual Studio 可讓您使用設計工具設計應用程式頁面。 設計工具會顯示主版頁面中定義的每個內容預留位置的內容區域。 您可以藉由將控制項拖曳至這些內容區域，來設計應用程式頁面。

## <a name="application-pages"></a>應用程式頁面
 應用程式頁面會在伺服器上的所有網站之間共用，而網站頁面則是專屬於某個網站。 如需詳細資訊，請查看[SharePoint 頁面類型](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))。

 根據預設，當您建立 SharePoint 網站時顯示的大部分頁面都是網站頁面。 網站頁面可以加入至 SharePoint 頁面文件庫。 使用者可以使用 SharePoint Designer 之類的工具來自訂網站頁面。 網站頁面也可以裝載諸如動態 Web 組件和 Web 元件區域之類的功能。

 應用程式頁面無法執行這些動作。 不過，如果您想要讓頁面包含自訂程式碼，應用程式頁面就是要建立的最佳頁面類型。 雖然您可以將自訂程式碼加入至網站頁面，但當使用者使用 SharePoint Designer 之類的工具自訂頁面時，程式碼就會停止執行。

> [!NOTE]
> Visual Studio 不會提供可協助您建立 SharePoint 網站網站頁面的範本。 如需詳細資訊，請參閱[SharePoint 頁面類型](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14))。

## <a name="create-an-application-page"></a>建立應用程式頁面
 若要建立應用程式頁面，請將**應用程式頁面**專案加入至 SharePoint 專案。 當您建立應用程式頁面時，Visual Studio 會將下列資料夾新增至您的專案：

|資料夾|描述|
|------------|-----------------|
|版面配置|對應至 SharePoint 檔案系統的 _layouts 虛擬目錄。|
|版面配置子資料夾|包含組成應用程式頁面的檔案。 根據預設，此資料夾與您的專案具有相同的名稱。 您可以隨時重新命名此資料夾。 當您執行專案時，Visual Studio 會將此資料夾部署至 SharePoint 檔案系統的 _layouts 虛擬目錄。|

 Visual Studio 會將下列檔案新增至您的專案：

|檔案|描述|
|----------|-----------------|
|ASP.NET 網頁檔案（ *.aspx*）|包含定義頁面的 XML 標記。|
|應用程式頁面程式碼檔案|包含應用程式頁面背後的程式碼。 將處理事件的程式碼加入至這個檔案。|
|應用程式頁面設計工具程式碼檔案|包含設計工具所產生的程式碼。 請勿直接編輯此檔案。|

## <a name="design-and-debug-an-application-page"></a>設計和 debug 應用程式頁面
 使用 Visual Studio 中的設計工具，設計應用程式頁面的內容。 這個設計工具會在您開啟專案中的應用程式頁面時顯示（按兩下它，或開啟其快捷方式功能表，然後選擇 [**開啟**]），然後選擇編輯器底部的 [**設計**] 按鈕。

> [!NOTE]
> 您只能在設計工具的 [**來源**] 視圖中設計頁面。 應用程式頁面的設計工具**設計**視圖已停用。

 您可以像處理 Visual Studio 中的其他 SharePoint 專案專案一樣，進行應用程式頁面的 debug。 當您啟動 [Visual Studio 偵錯工具] 時，Visual Studio 會開啟 SharePoint 網站。

 若要查看應用程式頁面，您必須手動流覽至應用程式頁面的位置（例如： HTTP://<em>Server_Name</em>/_Layouts/*Project_Name*/ApplicationPage1.aspx）。

 如需如何對 SharePoint 專案進行偵錯工具的詳細資訊，請參閱針對[sharepoint 方案進行疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。

## <a name="choose-a-master-page"></a>選擇主版頁面
 根據預設，**應用程式頁面**專案會參考您用來對專案進行 debug 的網站主版頁面。 該頁面命名為 [v4. master]，您可以在 SharePoint 網站的**主版頁面圖庫**中找到它。

 您可以藉由設定應用程式 `Page` 元素的 `MasterPageFile` 屬性，明確變更應用程式頁面所使用的主版頁面。 （例如： `MasterPageFile="~/_layouts/applicationv4.master"`）。 事實上，如果 SharePoint 伺服器上未啟用動態主版頁面，您就必須設定這個屬性。 如需 SharePoint 主版頁面的詳細資訊，請參閱[主版頁面](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))。

## <a name="see-also"></a>請參閱
- [深入瞭解 SharePoint Foundation 開發](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [ASP.NET 概觀](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index)
