---
title: 建立 SharePoint 頁面 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628360"
---
# <a name="create-pages-for-sharepoint"></a>建立 SharePoint 頁面
  您可以建立應用程式頁面、 網頁、 主版頁面和頁面配置的 SharePoint 網站。

 您可以在 Visual Studio 中使用範本建立應用程式頁面。 使用 SharePoint Designer 建立網頁、 主版頁面和頁面配置。 然後，您可以將這些頁面匯 Visual Studio SharePoint 專案中使用它們。

 您也可以使用階層式樣式表、 ECMAScript 和佈景主題，修改的外觀和行為的頁面。

## <a name="types-of-sharepoint-pages"></a>類型的 SharePoint 頁面
 下表描述四種的主要類型的 SharePoint 網站包含的頁數。

|頁面類型|描述|
|---------------|-----------------|
|應用程式頁面|如果您想要的頁面，以包含自訂程式碼，或您想要的頁面，即可在多個站台之間共用，請建立應用程式頁面。 否則，網站頁面可能是最佳的選擇。|
|網站頁面|如果您想要執行任何下列的工作，請建立網站頁面：<br /><br /> -將頁面加入 SharePoint 文件庫。<br />-啟用主機功能，例如動態的 Web 組件和網頁組件區域頁面。<br />-可讓使用者可以使用 SharePoint Designer 自訂頁面。<br /><br /> 如果您想要的頁面，以包含自訂程式碼，請不要建立的網站頁面。 雖然您可以在站台 頁面中加入自訂程式碼，程式碼會停止執行時的使用者使用 SharePoint Designer 自訂頁面。|
|主版頁面|建立主版頁面，如果您想要定義網頁的通用結構和應用程式頁面。|
|頁面配置|頁面版面配置特有[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]並可讓您進一步定義網頁和應用程式頁面的一般結構。|

 如需每種頁面的概觀，請參閱[建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)，並[頁面上的版面配置和主版頁面](http://go.microsoft.com/fwlink/?LinkID=182096)。

## <a name="create-application-pages"></a>建立應用程式頁面
 您可以在 Visual Studio 中建立應用程式頁面，藉由新增**應用程式頁面**至 SharePoint 專案項目。 您可以將控制項加入至頁面上，並加入程式碼，以處理控制項事件。

 您可以在頁面的程式碼檔案中設定中斷點、 開始偵錯工具，和測試本機 SharePoint 網站上的頁面，而不執行任何其他設定步驟。 如需詳細資訊，請參閱 < [for SharePoint 建立應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

## <a name="create-site-pages-master-pages-and-page-layouts"></a>建立網頁、 主版頁面和頁面配置
 您可以使用 SharePoint Designer 來建立網站頁面、 主版頁面和頁面配置。 然後，您可以將這些頁面匯 Visual Studio。 如果您想要充分利用原始檔控制功能，可在 Visual Studio 中的部署，請匯入您的頁面。 如需詳細資訊，請參閱 <<c0> [ 匯入現有的 SharePoint 網站中的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。

 因為很難修改這些頁面，您將它們匯入之後，您應該在匯入它們之前，設計這些頁面。

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>建立階層式樣式表、 ECMAScript 和佈景主題
 Visual Studio 不提供開發階層式樣式表 (CSS)、 ECMAScript （JavaScript、 JScript） 或 SharePoint 網站的佈景主題檔案的範本。 使用 SharePoint SDK 中提供的指引，或使用 SharePoint Designer 之類的工具，您可以建立這些檔案。

 您可以直接將這些檔案新增到您的解決方案，或者您可以匯入它們。 在任一情況下，您必須建立每個項目加入適當的對應的資料夾。 如需如何建立對應的資料夾的詳細資訊，請參閱[如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

 如需建立階層式樣式表的詳細資訊，請參閱 <<c0> [ 在 SharePoint Foundation 中階層式樣式表類別使用量](http://go.microsoft.com/fwlink/?LinkID=182098)。 如需建立 SharePoint 方案的 JavaScript 和 JScript 檔案的詳細資訊，請參閱[設定註冊的基本 ASPX 頁面的 ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099)。 如需佈景主題的詳細資訊，請參閱[建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[建立 SharePoint 相關應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)|描述如何新增應用程式頁面： *.aspx*會與 SharePoint 主版頁面合併的內容。|
|[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)|說明如何建立 SharePoint 網站執行的 ASP.NET 網頁。|
|[逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|說明如何設計和偵錯 ASP.NET 網頁中的 SharePoint 網站。|
