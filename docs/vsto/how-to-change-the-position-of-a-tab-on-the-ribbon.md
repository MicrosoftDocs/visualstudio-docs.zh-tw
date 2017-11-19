---
title: "如何： 變更功能區上的索引標籤的位置 |Microsoft 文件"
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40907d71bae8c8c25f06b3b1f3d4af8b9f79c385
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>如何：變更功能區索引標籤的位置
  您可以使用，以變更功能區上的自訂索引標籤的順序**索引標籤集合編輯器**。 在功能區上的內建索引標籤的前後，您可以將自訂索引標籤。 內建索引標籤是已在 Microsoft Office 應用程式的功能區的索引標籤。 例如，**資料** 索引標籤是在 Excel 中的內建索引標籤。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>若要變更的功能區上的索引標籤順序  
  
1.  在 [選取功能區程式碼檔案 （.vb 或.cs 檔案）**方案總管] 中**。  
  
2.  在**檢視**功能表上，按一下 **設計師**。  
  
3.  功能區設計工具中，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
4.  在**屬性**視窗中，選取**索引標籤**屬性，然後按一下省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile設計工具橢圓形"))。  
  
     **索引標籤集合編輯器**隨即出現。  
  
5.  在**索引標籤集合編輯器**，請在**成員**清單中，選取您要移動，然後按一下向上或向下箭號，變更定位順序的索引標籤。  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>之前或之後的內建索引標籤功能區上放置索引標籤  
  
1.  在功能區設計工具中，選取自訂索引標籤。  
  
2.  中**屬性**視窗中，展開**ControlId**屬性，然後確定值**ControlIdType**屬性設定為**自訂**.  
  
3.  在**屬性**視窗中，展開 **位置**屬性。  
  
4.  設定**PositionType**屬性設為適當值：  
  
    -   **BeforeOfficeId**放置之前指定的內建索引標籤的群組。  
  
    -   **AfterOfficeId**將群組放置在指定的內建索引標籤之後。  
  
5.  設定**OfficeId**內建索引標籤的控制項 ID 的屬性。  
  
     如需控制項 Id 的清單，請參閱[Office 2010 說明檔： Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  