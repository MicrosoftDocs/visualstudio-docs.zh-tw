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
ms.openlocfilehash: 815d48d7e7874ea5bd34d840ceecadcc4edb8dda
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865069"
---
# <a name="create-application-pages-for-sharepoint"></a>建立 SharePoint 相關應用程式頁面
  *應用程式頁面*是 ASP.NET 網頁，專為在 SharePoint 網站中使用。 應用程式頁面是 ASP.NET 網頁的特殊化的類型。 應用程式頁面和標準的 ASP.NET 網頁的主要差異是應用程式頁面包含與 SharePoint 主版頁面合併的內容。 主版頁面可讓應用程式頁面來做為站台的其他頁面共用相同的外觀和行為。  
  
 Visual Studio 可讓您使用設計工具設計應用程式頁面。 設計工具會顯示主版頁面中定義每個內容預留位置的內容區域。 您可以設計應用程式頁面上，將控制項拖曳至這些內容的區域。  
  
## <a name="application-pages"></a>應用程式頁面
 應用程式頁面會共用在伺服器上的所有站台，而網站頁面是一個站台所特有。 如需詳細資訊， [SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
 根據預設，當您建立 SharePoint 網站時出現的頁面的大部分都是網站頁面。 站台 頁面可加入 SharePoint 頁面文件庫。 使用者可以使用 SharePoint Designer 之類的工具，以自訂的網站頁面。 網站頁面也可以裝載功能，例如動態的 Web 組件和網頁組件區域。  
  
 應用程式頁面無法執行這些動作。 不過應用程式頁面會是頁面的最佳的類型，即可建立您若希望以包含自訂程式碼頁面。 雖然您可以在站台 頁面中加入自訂程式碼，程式碼時停止執行使用者自訂的頁面，藉由使用 SharePoint Designer 之類的工具。  
  
> [!NOTE]  
>  Visual Studio 不提供範本，可協助您建立 SharePoint 網站的網站頁面。 如需詳細資訊，請參閱 < [SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## <a name="create-an-application-page"></a>建立應用程式頁面
 若要建立應用程式頁面上，新增**應用程式頁面**至 SharePoint 專案項目。 當您建立應用程式頁面時，Visual Studio 會加入至您的專案的下列資料夾：  
  
|資料夾|描述|  
|------------|-----------------|  
|版面配置|會對應至 SharePoint 檔案系統的 _layouts 虛擬目錄。|  
|配置的子資料夾|包含組成應用程式頁面上的檔案。 根據預設，此資料夾會含有與專案相同的名稱。 您可以隨時重新命名此資料夾。 當您執行專案時，Visual Studio 會部署到 SharePoint 檔案系統的 _layouts 虛擬目錄的此資料夾。|  
  
 Visual Studio 會將您的專案中的下列檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|ASP.NET 網頁檔案 (*.aspx*)|包含 XML 標記定義頁面。|  
|應用程式頁面程式碼檔案|包含應用程式頁面背後的程式碼。 新增程式碼來處理此檔案的事件。|  
|應用程式頁面設計工具程式碼檔案|包含設計工具所產生的程式碼。 不要直接編輯這個檔案。|  
  
## <a name="design-and-debug-an-application-page"></a>設計和偵錯應用程式頁面
 在 Visual Studio 中使用設計工具檢視中設計應用程式頁面的內容。 此設計工具隨即出現，當您在專案中開啟應用程式頁面 (按兩下它，或開啟其捷徑功能表，然後選擇**開啟**)，然後選擇**設計**底部的按鈕編輯器。  
  
> [!NOTE]  
>  您可以設計頁面只能在**來源**設計工具的檢視。 **設計**設計工具檢視已停用應用程式頁面。  
  
 就像您會偵錯在 Visual Studio 中的其他 SharePoint 專案項目，您可以偵錯應用程式頁面。 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。  
  
 若要檢視應用程式頁面上，您必須以手動方式瀏覽至應用程式頁面的位置 (例如： http://<em>Server_Name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx)。  
  
 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="choose-a-master-page"></a>選擇主版頁面
 根據預設，**應用程式頁面**項目會參考您用來偵錯您的專案網站的主版頁面。 頁面命名為 v4.master，您可以找到它列在**主版頁面圖庫**的 SharePoint 網站。  
  
 您可以明確地變更的主版頁面藉由設定時由應用程式頁面`MasterPageFile`應用程式的屬性`Page`項目。 (例如： `MasterPageFile="~/_layouts/applicationv4.master"`)。 事實上，您必須先設定這個屬性，如果 SharePoint 伺服器上未啟用動態主版頁面。 如需有關在 SharePoint 中的主版頁面的詳細資訊，請參閱 <<c0> [ 主版頁面](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## <a name="see-also"></a>另請參閱
 [SharePoint Foundation 深入開發](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET 概觀](/aspnet/overview)   
 [ASP.NET Web Pages](/aspnet/web-pages/index)   
