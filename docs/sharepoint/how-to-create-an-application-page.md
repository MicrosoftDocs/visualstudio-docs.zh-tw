---
title: 如何： 建立應用程式頁面 |Microsoft 文件
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a95a7e08a52ff2b6d20f3e84f7456c37e8901ab2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-application-page"></a>如何：建立應用程式頁面
  您可以為一個或多個 SharePoint 網站建立 ASP.NET 網頁。 在 SharePoint 中，這些頁面會呼叫應用程式頁面。 不同於網站頁面上，應用程式頁面上會包含程式碼執行後置頁面。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
### <a name="to-create-an-application-page"></a>若要建立的應用程式頁面  
  
1.  在 Visual Studio 中開啟或建立 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 [ **方案總管**] 中選擇專案節點。  
  
3.  在功能表列上選擇 **專案**，**加入新項目**。  
  
4.  在**加入新項目**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**項目。  
  
5.  在 SharePoint 範本清單中選擇**應用程式頁面**。  
  
6.  在**名稱**方塊，應用程式頁面上，為指定的名稱，然後選擇**新增** 按鈕。  
  
     Visual Studio 會將數個資料夾和檔案加入至您的專案。 如需有關這些檔案的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
     在**來源**Visual Web Developer 設計工具中，ASP.NET 網頁檔案的檢視會出現。 您可以加入的控制項來設計頁面**工具箱**並將它們放置在內容預留位置上。 如需詳細資訊，請參閱[來源檢視、 Web 網頁設計工具](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f)。  
  
7.  若要處理控制項事件，請將程式碼加入至應用程式頁面的程式碼檔案。  
  
     如果您展開 ASP.NET 網頁檔案的節點，程式碼檔案就會出現，且根據專案語言而定，其副檔名會是 .cs 或 .vb。 如何建立應用程式頁面上的端對端範例，請參閱[逐步解說： 建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SharePoint 應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  