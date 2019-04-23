---
title: HOW TO：建立使用者控制項為 SharePoint 應用程式頁面或 Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6e0cc6ee8df5285555760521b415ce8f6679fc2f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072041"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>HOW TO：建立 SharePoint 應用程式頁面或 web 組件的使用者控制項
  您可以建立自訂使用者控制項，為 SharePoint 方案提供自訂功能，而且您可以在專案內重複使用該功能。 您可以將 Web 組件或應用程式頁面中加入使用者控制項，或加入其他 ASP.NET 控制項和 SharePoint 控制項，並且定義控制項的屬性和方法。 如需有關使用者控制項的詳細資訊，請參閱 <<c0> [ 建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)並[使用者控制項和 SharePoint 中的伺服器控制項](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)。

### <a name="to-create-a-user-control-for-sharepoint"></a>若要建立適用於 SharePoint 的使用者控制項

1. 在 Visual Studio 中開啟或建立 SharePoint 專案。

     請參閱[SharePoint 專案和專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在 [ **方案總管**] 中選擇專案節點。

3. 在功能表列中，選擇 [專案] > [加入新項目]。

     [新增項目] 對話方塊隨即開啟。

4. 在 **已安裝**窗格中，選擇**Office/SharePoint**節點。

5. 在 SharePoint 範本清單中，選擇**使用者控制項 （僅限陣列方案）**。

    > [!NOTE]
    >  使用者控制項只適用於陣列方案。

6. 在 [**名稱**方塊，使用者控制項，為指定的名稱，然後選擇**新增**] 按鈕。

     Visual Studio 會將數個資料夾和檔案加入至您的專案。 如需有關這些檔案的詳細資訊，請參閱 <<c0> [ 建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

     根據預設，使用者控制項檔案會出現在**來源**Visual Web Developer 設計工具的檢視。 在這個檢視中，您可以編輯控制項的 XML 標記。 您可以切換到**設計**如果您想要以視覺化方式設計控制項，藉由拖曳的控制項檢視**工具箱**。 請參閱[設計檢視中，Web 網頁設計工具](/previous-versions/aspnet/ms178149\(v\=vs.100\))。

7. 如果您想要處理在控制項中發生的事件，請在使用者控制項的程式碼檔案中加入程式碼。

     此檔案會出現在**方案總管] 中**下方 [使用者控制項檔案且具有 *.cs*或 *.vb*延伸模組，根據專案的語言。

## <a name="see-also"></a>另請參閱
- [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [建立 SharePoint 相關應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)
