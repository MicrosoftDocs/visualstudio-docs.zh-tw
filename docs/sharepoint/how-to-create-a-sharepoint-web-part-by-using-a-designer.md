---
title: 如何：使用設計工具建立 SharePoint Web 元件 |Microsoft Docs
titleSuffix: ''
description: 藉由將視覺 web 元件專案加入至 SharePoint 專案來建立網頁元件，該專案會在 Visual Studio 中開啟 Visual Web Developer designer。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14f6add337ecfae3ab0dc5aa77a72962f2a0a915
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851591"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>如何：使用設計工具建立 SharePoint Web 元件
  您可以藉由將 **視覺 Web 元件** 專案加入至任何 SharePoint 專案，來建立網頁元件。 這會開啟 [Visual Studio 中的 Visual Web Developer designer，您可以在其中將控制項和程式碼新增至網頁元件。 視覺網頁元件的運作方式與 web 元件相同。 唯一的差別在於，您可以在 Visual Web Developer 設計工具中設計視覺化網頁元件。

### <a name="to-create-a-project-for-visual-web-parts"></a>若要建立視覺 web 元件的專案

1. 在功能表列上 **，選擇 [** 檔案  > **新增**  >  **專案**]。

     此時會開啟 [新增專案] 對話方塊。

2. 在 [ **新增專案** ] 對話方塊的 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **Office/SharePoint** ] 節點，然後選擇 [ **SharePoint 方案** ] 類別。

3. 在專案範本清單中，選擇 [ **SharePoint 2013-視覺 Web 元件**]，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。

4. 在 [ **指定偵錯工具的網站和安全性等級** ] 頁面上，指定本機電腦上的 SHAREPOINT 網站 URL，然後選擇 [ **完成]** 按鈕。

     在 **方案總管** 中，會顯示網頁元件。 在 Visual Web Developer designer 中設計網頁元件之後，您將在指定的網站上進行測試。

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>將視覺網頁元件加入至現有的 SharePoint 專案

1. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

2. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **Office/SharePoint** ] 節點。

3. 在專案範本清單中，選擇 [ **視覺網頁元件**]、[命名]，然後選擇 [ **加入** ] 按鈕。

     在 **方案總管** 中，您的網頁元件隨即出現。 在 Visual Web Developer designer 中設計網頁元件之後，您將在指定的網站上進行測試。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [逐步解說：建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [逐步解說：使用設計工具建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
