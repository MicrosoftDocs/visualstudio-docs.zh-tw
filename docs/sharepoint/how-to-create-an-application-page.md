---
title: 如何：建立應用程式頁面 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 32e6fbb7cece4c3b7513dfc1f5de3aca22f145ee
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016947"
---
# <a name="how-to-create-an-application-page"></a>如何：建立應用程式頁面
  您可以為一個或多個 SharePoint 網站建立 ASP.NET 網頁。 在 SharePoint 中，這些頁面稱為應用程式頁面。 不同于網站頁面，應用程式頁面包含在頁面後方執行的程式碼。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

### <a name="to-create-an-application-page"></a>若要建立應用程式頁面

1. 在 Visual Studio 中開啟或建立 SharePoint 專案。

     如需詳細資訊，請參閱[SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在 [ **方案總管**] 中選擇專案節點。

3. 在功能表列上，選擇 [**專案**] [  >  **加入新專案**]。

4. 在 [**加入新專案**] 對話方塊中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 專案。

5. 在 SharePoint 範本清單中，選擇 [**應用程式頁面**]。

6. 在 [**名稱**] 方塊中，指定應用程式頁面的名稱，然後選擇 [**新增**] 按鈕。

     Visual Studio 會在專案中加入數個資料夾和檔案。 如需這些檔案的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

     在 Visual Web Developer 設計工具的 [**來源**] 視圖中，會顯示 ASP.NET 網頁檔。 您可以從 [**工具箱**] 新增控制項，並將其放在內容預留位置上，以設計頁面。 如需詳細資訊，請參閱[來源視圖、Web 網頁設計](/previous-versions/aspnet/ms178154\(v\=vs.100\))工具。

7. 若要處理控制項事件，請將程式碼加入至應用程式頁面的程式碼檔案。

     如果您展開 ASP.NET 網頁檔案的節點，且其副檔名為 *.cs*或 *.vb* ，則會出現程式碼檔案，視專案的語言而定。 如需如何建立應用程式頁面的端對端範例，請參閱逐步解說[：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
