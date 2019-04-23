---
title: HOW TO：建立應用程式頁面 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb5c4d7497525706384ced52caae1ba8e02f3e23
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063019"
---
# <a name="how-to-create-an-application-page"></a>HOW TO：建立應用程式頁面
  您可以為一個或多個 SharePoint 網站建立 ASP.NET 網頁。 在 SharePoint 中，這些頁面會呼叫應用程式頁面。 不同站台 頁面中，於應用程式頁面會包含後置頁面執行的程式碼。 如需詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

### <a name="to-create-an-application-page"></a>若要建立應用程式頁面

1. 在 Visual Studio 中開啟或建立 SharePoint 專案。

     如需詳細資訊，請參閱 < [SharePoint 專案和專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在 [ **方案總管**] 中選擇專案節點。

3. 在功能表列中，選擇 [專案] > [加入新項目]。

4. 在**加入新項目**對話方塊方塊中，展開**SharePoint**節點，然後選擇**2010年**項目。

5. 在 SharePoint 範本清單中，選擇**應用程式頁面**。

6. 在 **名稱**方塊，應用程式 頁面中，為指定的名稱，然後選擇**新增** 按鈕。

     Visual Studio 會將數個資料夾和檔案加入至您的專案。 如需有關這些檔案的詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

     在 **來源**Visual Web Developer 設計工具中，ASP.NET 網頁檔案的檢視會出現。 您可以透過加入控制項，從設計頁面**工具箱**並將它們放置在內容預留位置上。 如需詳細資訊，請參閱 <<c0> [ 來源檢視，網頁設計師](/previous-versions/aspnet/ms178154\(v\=vs.100\))。

7. 若要處理控制項事件，請將程式碼加入至應用程式頁面的程式碼檔案。

     當您展開 ASP.NET 網頁檔案的節點會出現的程式碼檔案，並已 *.cs*或是 *.vb*延伸模組，根據專案的語言。 如何建立應用程式頁面的端對端範例，請參閱[逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 相關應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
