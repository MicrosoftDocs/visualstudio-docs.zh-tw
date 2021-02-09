---
title: 如何：建立 SharePoint Web 元件 |Microsoft Docs
description: 使用設計工具建立和自訂網頁元件，或將 web 元件專案加入至任何 SharePoint 專案，然後編輯 web 元件的程式碼檔案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f15cd788d19540bdea416b36ab0f8e8d8aa95e3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925600"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>如何：建立 SharePoint web 元件
  您可以建立和自訂網頁元件，方法是將 **網頁元件** 專案加入至任何 SharePoint 專案，然後編輯 web 元件的程式碼檔案，或使用設計工具。 如需詳細資訊，請參閱 [如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。

### <a name="to-create-a-sharepoint-web-part"></a>若要建立 SharePoint web 元件

1. 建立或開啟 SharePoint 專案。

     如需詳細資訊，請參閱 [SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2. 在 **方案總管** 中選擇 SharePoint 專案節點，然後選擇 [**專案**  >  **加入新專案**]。

3. 在 [ **加入新專案** ] 對話方塊中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 SharePoint 範本清單中，選擇 [ **Web 元件**]。

5. 在 [ **名稱** ] 方塊中，指定網頁元件的名稱，然後選擇 [ **加入** ] 按鈕。

     Web 元件會出現在 **方案總管** 中。 如需網頁元件所包含檔案的詳細資訊，請參閱 [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)。

6. 在 **方案總管** 中，開啟您剛才建立之 web 元件的程式碼檔案。

     例如，如果您的網頁元件名稱是 *WebPart1*，請在 Visual Basic) 中開啟 [ *WebPart1* ] (，或在 c # ) 中開啟 *WebPart1.cs* (。

7. 在程式碼檔案中，將控制項加入至 <xref:System.Web.UI.Control.CreateChildControls%2A> 方法。

     如需範例，請參閱 [逐步解說：建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [如何：使用設計工具建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [逐步解說：建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [逐步解說：使用設計工具建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
