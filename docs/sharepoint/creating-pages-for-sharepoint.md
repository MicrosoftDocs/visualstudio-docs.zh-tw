---
title: 建立 SharePoint 的頁面 |Microsoft Docs
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
ms.openlocfilehash: 297ebf0e7c2ed1273dd5a8ac973ce497c4c64781
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986346"
---
# <a name="create-pages-for-sharepoint"></a>建立 SharePoint 的頁面
  您可以建立 SharePoint 網站的應用程式頁面、網站頁面、主版頁面和頁面配置。

 您可以使用 Visual Studio 中的範本來建立應用程式頁面。 使用 SharePoint Designer 來建立網站頁面、主版頁面和頁面配置。 然後，您可以將這些頁面匯入 Visual Studio，以便在 SharePoint 專案中使用它們。

 您也可以使用級聯樣式表、ECMAScript 和主題來修改頁面的外觀和行為。

## <a name="types-of-sharepoint-pages"></a>SharePoint 頁面的類型
 下表描述 SharePoint 網站包含的四種主要頁面類型。

|頁面類型|描述|
|---------------|-----------------|
|應用程式頁面|如果您想要頁面包含自訂程式碼，或想要在多個網站之間共用網頁，請建立應用程式頁面。 否則，網站頁面可能是最佳選擇。|
|網站頁面|如果您想要執行下列任何一項工作，請建立網站頁面：<br /><br /> -將頁面新增至 SharePoint 文件庫。<br />-啟用頁面來裝載功能，例如動態 Web 組件和 Web 元件區域。<br />-讓使用者能夠使用 SharePoint Designer 來自訂頁面。<br /><br /> 如果您想要讓頁面包含自訂程式碼，請勿建立網站頁面。 雖然您可以將自訂程式碼加入至網站頁面，但當使用者使用 SharePoint Designer 自訂頁面時，程式碼就會停止執行。|
|主版頁面|如果您想要定義網站頁面和應用程式頁面的通用結構，請建立主版頁面。|
|頁面配置|頁面配置是 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 特有的，可讓您進一步定義網站頁面和應用程式頁面的通用結構。|

 如需每種頁面類型的總覽，請參閱[建立區塊：頁面和使用者介面](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))，以及[頁面配置和主版頁面](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14))。

## <a name="create-application-pages"></a>建立應用程式頁面
 您可以藉由將**應用程式頁面**專案新增至 SharePoint 專案，在 Visual Studio 中建立應用程式頁面。 您可以將控制項加入至頁面，然後藉由加入程式碼來處理控制項事件。

 您可以在頁面的程式碼檔案中設定中斷點，啟動偵錯工具，並在本機 SharePoint 網站上測試頁面，而不需要執行任何額外的設定步驟。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

## <a name="create-site-pages-master-pages-and-page-layouts"></a>建立網站頁面、主版頁面和頁面配置
 您可以使用 SharePoint Designer 來建立網站頁面、主版頁面和頁面配置。 然後，您可以將這些頁面匯入 Visual Studio。 如果您想要利用 Visual Studio 中提供的部署或原始檔控制功能，請匯入您的頁面。 如需詳細資訊，請參閱[從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。

 因為您在匯入這些頁面之後很難以修改它們，所以您應該先設計這些頁面，再將它們匯入。

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>建立級聯樣式表、ECMAScript 和主題
 Visual Studio 不會提供用來開發 SharePoint 網站階層式樣式表（CSS）、ECMAScript （JavaScript、JScript）或主題檔案的範本。 您可以使用 SharePoint SDK 中提供的指導方針，或使用 SharePoint Designer 之類的工具來建立這些檔案。

 您可以直接將這些檔案新增至您的方案，也可以將它們匯入。 不論是哪一種情況，您都必須針對您新增的每個專案建立適當的對應資料夾。 如需如何建立對應資料夾的詳細資訊，請參閱[如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

 如需建立階層式樣式表的詳細資訊，請參閱[階層式樣式表 SharePoint Foundation 中的類別使用方式](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14))。 如需建立 SharePoint 方案的 JavaScript 和 JScript 檔案的詳細資訊，請參閱[設定 ECMAScript 的基本 ASPX 頁面](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14))。 如需主題的詳細資訊，請參閱[建立區塊：頁面和使用者介面](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)|描述如何加入應用程式頁面：與 SharePoint 主版頁面合併的 *.aspx*內容。|
|[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)|說明如何建立在 SharePoint 網站上執行的 ASP.NET 網頁。|
|[逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|說明如何設計和 ASP.NET SharePoint 網站的網頁。|
