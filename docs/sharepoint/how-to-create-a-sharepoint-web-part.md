---
title: "如何： 建立 SharePoint Web 組件 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847124dc9a7e4cd80993df5b50c5d3d3b752f228
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-web-part"></a>如何：建立 SharePoint Web 組件
  您可以建立並自訂 web 組件加入**Web 組件**至任何 SharePoint 專案項目，然後編輯 web 組件，或使用設計工具的程式碼檔。 如需詳細資訊，請參閱[How to： 使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
### <a name="to-create-a-sharepoint-web-part"></a>若要建立 SharePoint Web 組件  
  
1.  建立或開啟 SharePoint 專案。  
  
     如需詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  選擇 SharePoint 專案節點中的**方案總管] 中**，然後選擇 [**專案**，**加入新項目**。  
  
3.  在**加入新項目**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**節點。  
  
4.  在 SharePoint 範本清單中選擇**Web 組件**。  
  
5.  在**名稱**方塊，指定 web 組件的名稱，然後選擇**新增** 按鈕。  
  
     Web 組件會出現在**方案總管 中**。 如需 web 組件包含的檔案的詳細資訊，請參閱[建立 sharepoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
6.  在**方案總管 中**，開啟您剛才建立的 web 組件的程式碼檔案。  
  
     例如，如果 Web 組件名稱為 WebPart1，則開啟 WebPart1.vb (在 Visual Basic 中) 或 WebPart1.cs (在 C# 中)。  
  
7.  在程式碼檔案中，將控制項加入至 <xref:System.Web.UI.Control.CreateChildControls%2A> 方法。  
  
     如需範例，請參閱[逐步解說： 建立 SharePoint Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SharePoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何： 使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [逐步解說： 建立 SharePoint Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  