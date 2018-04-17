---
title: 建立 SharePoint 應用程式頁面 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68731e2a0c933f3f48f3a2211a9d17ca21e50242
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-application-pages-for-sharepoint"></a>建立 SharePoint 的應用程式頁面
  *應用程式頁面*是設計用來在 SharePoint 網站中使用 ASP.NET Web 網頁。 應用程式頁面是特殊的類型的 ASP.NET 網頁。 應用程式頁面和標準的 ASP.NET 網頁的主要差異是應用程式頁面上包含合併 SharePoint 主版頁面的內容。 主版頁面可讓應用程式頁面來做為站台的其他頁面共用相同的外觀和行為。  
  
 Visual Studio 可讓您使用設計工具設計應用程式頁面。 在設計工具會顯示內容區域定義主版頁面中每個內容預留位置。 您可以設計應用程式頁面上，將控制項拖曳到這些內容區域。  
  
## <a name="application-pages"></a>應用程式頁面  
 應用程式頁面會共用所有的站台伺服器上，而是一個站台的特定網站頁面。 如需詳細資訊， [SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
 根據預設，會顯示當您建立 SharePoint 網站之頁面的大部分都是網站頁面。 站台頁面可以加入至 SharePoint 頁面文件庫。 使用者可以使用 SharePoint Designer 之類的工具，以自訂網站頁面。 站台頁面也可以裝載功能，例如動態 Web 組件和網頁組件區域。  
  
 應用程式頁面無法執行這些動作。 不過應用程式頁面上會是頁面的最佳，即可建立您若希望以包含自訂程式碼頁面類型。 雖然您可以將自訂程式碼加入至網站頁面，程式碼會停止執行時的使用者自訂頁面使用 SharePoint Designer 之類的工具。  
  
> [!NOTE]  
>  Visual Studio 不會提供範本，可協助您建立 SharePoint 網站的網站頁面。 如需詳細資訊，請參閱[SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## <a name="creating-an-application-page"></a>建立應用程式頁面  
 若要建立應用程式頁面上，新增**應用程式頁面**加入 SharePoint 專案項目。 當您建立的應用程式頁面時，Visual Studio 會在您的專案中加入下列資料夾：  
  
|資料夾|描述|  
|------------|-----------------|  
|版面配置|對應到 SharePoint 檔案系統的 _layouts 虛擬目錄。|  
|配置的子資料夾|包含組成應用程式頁面上的檔案。 根據預設，此資料夾含有與專案相同的名稱。 您可以隨時重新命名此資料夾。 當您執行專案時，Visual Studio 會部署這個資料夾 SharePoint 檔案系統的 _layouts 虛擬目錄。|  
  
 Visual Studio 會在您的專案中加入下列檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|ASP.NET 網頁檔案 (.aspx)|包含定義頁面的 XML 標記。|  
|應用程式頁面的程式碼檔|包含程式碼後置應用程式頁面。 加入程式碼可處理此檔案的事件。|  
|應用程式頁面的設計工具程式碼檔|包含設計工具所產生的程式碼。 不要直接編輯這個檔案。|  
  
## <a name="designing-and-debugging-an-application-page"></a>設計和偵錯的應用程式頁面  
 使用設計工具檢視 Visual Studio 中設計的應用程式頁面的內容。 此設計工具隨即出現，當您在專案中開啟應用程式頁面 (透過按兩下，或是開啟其捷徑功能表，然後選擇**開啟**)，然後選擇 [**設計**底部的按鈕編輯器]。  
  
> [!NOTE]  
>  您可以設計頁面只有在**來源**設計工具的檢視。 **設計**設計工具檢視應用程式頁面已停用。  
  
 您可以偵錯應用程式頁面上，就像您會偵錯 Visual Studio 中的其他 SharePoint 專案項目。 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。  
  
 若要檢視應用程式頁面上，您必須以手動方式巡覽至應用程式頁面上的位置 (例如： http://*Server_Name*/_layouts/*Project_Name*/ApplicationPage1.aspx)。  
  
 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="choosing-a-master-page"></a>選擇主版頁面  
 根據預設，**應用程式頁面**項目參考的主版頁面的站台用來偵錯您的專案。 頁面名為 v4.master，而且您可以找到它列在**主版頁面圖庫**的 SharePoint 網站。  
  
 您可以明確地變更的主版頁面所設定使用的應用程式頁面`MasterPageFile`應用程式的屬性`Page`項目。 (例如： `MasterPageFile="~/_layouts/applicationv4.master"`)。 事實上，您必須將此屬性，如果在 SharePoint 伺服器上未啟用動態主版頁面。 如需有關在 SharePoint 中的主版頁面的詳細資訊，請參閱[主版頁面](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint Foundation 開發深度](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET 概觀](/aspnet/overview)   
 [ASP.NET Web Pages](/aspnet/web-pages/index)   
  
  