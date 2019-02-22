---
title: HOW TO：建立 SharePoint Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3328c8900a202dd28eb2cab7c9651de8f45aa35e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636914"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>HOW TO：建立 SharePoint web 組件
  您可以建立並自訂 web 組件，藉由新增**Web 組件**至任何 SharePoint 專案項目，然後再編輯 web 組件，或使用設計工具的程式碼檔案。 如需詳細資訊，請參閱[如何：使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。

### <a name="to-create-a-sharepoint-web-part"></a>若要建立 SharePoint web 組件

1.  建立或開啟 SharePoint 專案。

     如需詳細資訊，請參閱 < [SharePoint 專案和專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

2.  選擇 SharePoint 專案節點，在**方案總管**，然後選擇**專案** > **加入新項目**。

3.  在**加入新項目**對話方塊方塊中，展開**SharePoint**節點，然後選擇**2010年**節點。

4.  在 SharePoint 範本清單中，選擇**Web 組件**。

5.  在 [**名稱**方塊，指定 web 組件的名稱，然後選擇**新增**] 按鈕。

     Web 組件會出現在**方案總管 中**。 如需有關 web 組件包含的檔案的詳細資訊，請參閱[建立適用於 SharePoint 的 web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。

6.  在 [**方案總管] 中**，開啟您剛建立的 web 組件的程式碼檔案。

     例如，如果您的 web 組件的名稱是*WebPart1*，開啟*WebPart1.vb* （在 Visual Basic) 或*WebPart1.cs* （在 C# 中)。

7.  在程式碼檔案中，將控制項加入至 <xref:System.Web.UI.Control.CreateChildControls%2A> 方法。

     如需範例，請參閱[逐步解說：建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [如何：使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [逐步解說：建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [逐步解說：使用設計工具建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
