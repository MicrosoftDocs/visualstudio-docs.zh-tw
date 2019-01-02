---
title: HOW TO：將 XMLMappedRange 控制項加入工作表
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d7cc26c0170c2a20e27026ebcbc6d8705d34ce2
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646707"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>HOW TO：將 XMLMappedRange 控制項加入工作表
  當您將 XML 項目對應至 Microsoft Office Excel 中的資料格時，Visual Studio 會自動將<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項加入工作表。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項並不適用於**工具箱**或**Zdroje dat**視窗。 此外，您無法建立<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>以程式設計方式控制。  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>若要將 XMLMappedRange 控制項加入工作表  
  
1.  在 Visual Studio 設計工具中開啟 Excel 活頁簿。  
  
2.  開啟您要將控制項加入工作的表。  
  
3.  在 **開發人員**索引標籤上，按一下**來源**。  
  
    > [!NOTE]  
    >  如果**開發人員**功能區上看不到 [] 索引標籤中，您必須啟用它。 如需詳細資訊，請參閱[＜How to：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
     **XML 來源**工作窗格會顯示。  
  
4.  在  **XML 來源**工作窗格中，按一下**XML 對應**。  
  
5.  在 [ **XML 對應**] 對話方塊中，按一下**新增**。  
  
     **XML 來源** 對話方塊隨即出現。  
  
6.  選取 從 XML 結構描述**XML 來源**對話方塊，按一下**開啟**。  
  
     結構描述加入至**XML 對應** 對話方塊。  
  
7.  在 [ **XML 對應**] 對話方塊中，按一下**確定**。  
  
8.  拖曳項目從**XML 來源**工作表上的儲存格的工作窗格。  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>已建立並加入至專案。  
  
    > [!NOTE]  
    >  如果您將從父項目**XML 來源**工作窗格中，<xref:Microsoft.Office.Tools.Excel.ListObject>建立控制項。  
  
## <a name="see-also"></a>另請參閱  
 [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：將結構描述對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  