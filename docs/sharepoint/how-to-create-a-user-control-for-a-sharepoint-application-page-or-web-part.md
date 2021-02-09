---
title: 建立 SharePoint 應用程式頁面或 web 元件的使用者控制項
titleSuffix: ''
description: 建立自訂的使用者控制項，以提供 SharePoint 方案的自訂功能，並在 web 元件或應用程式頁面中重複使用該功能。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43386f3ba450058d6aaf8ab180e331d2f303a235
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925579"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>如何：為 SharePoint 應用程式頁面或 web 元件建立使用者控制項
  您可以建立自訂使用者控制項，為 SharePoint 方案提供自訂功能，而且您可以在專案內重複使用該功能。 您可以將 Web 組件或應用程式頁面中加入使用者控制項，或加入其他 ASP.NET 控制項和 SharePoint 控制項，並且定義控制項的屬性和方法。 如需使用者控制項的詳細資訊，請參閱為 [web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) ，以及 [SharePoint 中的使用者控制項和伺服器控制項](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)。

### <a name="to-create-a-user-control-for-sharepoint"></a>若要建立 SharePoint 的使用者控制項

1. 在 Visual Studio 中開啟或建立 SharePoint 專案。

     請參閱 [SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在 [ **方案總管**] 中選擇專案節點。

3. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

     [ **加入新專案** ] 對話方塊隨即開啟。

4. 在 [ **已安裝** ] 窗格中，選擇 [ **Office/SharePoint** ] 節點。

5. 在 SharePoint 範本清單中，選擇 [ **僅限使用者控制項 (伺服器陣列方案])**。

    > [!NOTE]
    > 使用者控制項只適用於陣列方案。

6. 在 [ **名稱** ] 方塊中，指定使用者控制項的名稱，然後選擇 [ **加入** ] 按鈕。

     Visual Studio 會將數個資料夾和檔案新增至您的專案。 如需這些檔案的詳細資訊，請參閱為 [web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

     根據預設，使用者控制項檔會出現在 Visual Web Developer designer 的 [ **來源** ] 視圖中。 在這個檢視中，您可以編輯控制項的 XML 標記。 如果您想要藉由從 [**工具箱**] 拖曳控制項以視覺化方式設計控制項，可以切換至 **設計** 視圖。 請參閱 [設計檢視、網頁設計](/previous-versions/aspnet/ms178149\(v\=vs.100\))工具。

7. 如果您想要處理在控制項中發生的事件，請在使用者控制項的程式碼檔案中加入程式碼。

     這個檔案會出現在使用者控制項檔的 **方案總管** 中，並具有 *.cs* 或 *.vb* 副檔名，視專案的語言而定。

## <a name="see-also"></a>另請參閱
- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
