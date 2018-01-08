---
title: "建立 SharePoint 的網頁 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7baa368e34b7b721e7b41c617c6ce6e89bb5f980
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-pages-for-sharepoint"></a>建立 SharePoint 的網頁
  您可以建立應用程式頁面、 網站頁面、 主版頁面和 SharePoint 網站的頁面配置。  
  
 您可以使用 Visual Studio 中的範本來建立應用程式頁面。 使用 SharePoint Designer 中建立網站頁面、 主版頁面和頁面配置。 然後，您可以匯入這些頁面 Visual Studio SharePoint 專案中使用它們。  
  
 您也可以使用階層式樣式表、 ECMAScript 和佈景主題，修改的外觀和行為的頁數。  
  
## <a name="types-of-sharepoint-pages"></a>類型的 SharePoint 頁面  
 下表描述四個主要類型的 SharePoint 網站所包含的頁數。  
  
|頁面類型|描述|  
|---------------|-----------------|  
|應用程式頁面|建立應用程式頁面上，如果您要讓頁面包含自訂程式碼，或想要跨多個站台共用頁。 否則，站台頁面可能會是最好的選擇。|  
|網站頁面|如果您想要執行任何下列工作，請建立網站頁面：<br /><br /> -將頁面加入 SharePoint 文件庫。<br />-啟用主機功能，例如動態 Web 組件和網頁組件區域頁面。<br />-可讓使用者可以使用 SharePoint Designer 自訂頁面。<br /><br /> 如果您想要以包含自訂程式碼，不要建立網站頁面。 雖然您可以將自訂程式碼加入至網站頁面，程式碼會停止執行時使用 SharePoint Designer 使用者可自訂的頁面。|  
|主版頁面|如果您想要定義站台網頁的通用結構主版頁面和應用程式頁面建立。|  
|頁面配置|頁面配置特有[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]並可讓您進一步定義站台的網頁和應用程式頁面的通用結構。|  
  
 如需每種類型的頁面的概觀，請參閱[建置組塊： 頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)，和[頁面配置和主版頁面](http://go.microsoft.com/fwlink/?LinkID=182096)。  
  
## <a name="creating-application-pages"></a>建立應用程式頁面  
 您也可以將 Visual Studio 中建立應用程式頁面**應用程式頁面**加入 SharePoint 專案項目。 您可以將控制項加入至頁面上，，然後加入程式碼中處理控制項事件。  
  
 您可以在頁面的程式碼檔案中設定中斷點、 開始偵錯工具，和測試本機 SharePoint 網站上的網頁，而不執行任何其他設定步驟。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>建立網站頁面、 主版頁面和頁面配置  
 您可以使用 SharePoint Designer 來建立網站頁面、 主版頁面和頁面配置。 然後，您可以匯入這些頁面 Visual Studio。 如果您想要充分利用可用在 Visual Studio 中的原始檔控制功能的部署，匯入您的網頁。 如需詳細資訊，請參閱[匯入現有的 SharePoint 網站中的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
 因為很難在匯入之後，修改這些頁面，您應該在您匯入之前，設計這些頁面。  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>建立階層式樣式表、 ECMAScript 和佈景主題  
 Visual Studio 不提供開發階層式樣式表 (CSS)、 ECMAScript （JavaScript、 JScript） 或 SharePoint 網站的佈景主題檔案的範本。 您可以使用 SharePoint SDK 中提供的指導方針，或使用 SharePoint Designer 之類的工具來建立這些檔案。  
  
 您可以直接將這些檔案加入至您的方案，或您可以匯入它們。 在任一情況下，您必須建立每個項目加入適當的對應的資料夾。 如需如何建立對應的資料夾的詳細資訊，請參閱[如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 如需建立階層式樣式表的詳細資訊，請參閱[階層式樣式表類別中的使用量 SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098)。 如需建立 SharePoint 方案的 JavaScript 和 JScript 檔案的詳細資訊，請參閱[設定 」 基本 ASPX 頁面的 ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099)。 如需佈景主題的詳細資訊，請參閱[建置組塊： 頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)|描述如何新增應用程式頁面： 會合併與 SharePoint 主版頁面的.aspx 內容。|  
|[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)|示範如何建立 SharePoint 網站執行的 ASP.NET 網頁。|  
|[逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|示範如何設計和偵錯 ASP.NET Web 網頁的 SharePoint 網站。|  
  
  