---
title: "如何： 將 XMLMappedRange 控制項加入工作表 |Microsoft 文件"
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
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d83241e265db0e0ef0165cbc1615f23ea2ec5a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>如何：將 XMLMappedRange 控制項加入至工作表
  當您將 XML 元素對應至 Microsoft Office Excel 中的資料格時，Visual Studio 會自動加入<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項加入工作表。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項並不適用於**工具箱**或**資料來源**視窗。 此外，您無法建立<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>以程式設計方式控制。  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>若要將 XMLMappedRange 控制項加入工作表  
  
1.  在 Visual Studio 設計工具中開啟 Excel 活頁簿。  
  
2.  開啟您要將控制項加入工作的表。  
  
3.  在**開發人員**索引標籤上，按一下 **來源**。  
  
    > [!NOTE]  
    >  如果**開發人員** 索引標籤沒有顯示功能區上，您必須啟用它。 如需詳細資訊，請參閱 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
     **XML 來源**工作窗格會顯示。  
  
4.  在**XML 來源**工作窗格中，按一下  **XML 對應**。  
  
5.  在**XML 對應**對話方塊中，按一下 **新增**。  
  
     **XML 來源** 對話方塊隨即出現。  
  
6.  選取 XML 結構描述從**XML 來源**對話方塊，按一下**開啟**。  
  
     結構描述加入至**XML 對應** 對話方塊。  
  
7.  在**XML 對應**對話方塊中，按一下 **確定**。  
  
8.  拖曳項目從**XML 來源**工作窗格加入工作表上的資料格。  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>已建立並加入至專案。  
  
    > [!NOTE]  
    >  如果您將從父項目拖曳**XML 來源**工作窗格<xref:Microsoft.Office.Tools.Excel.ListObject>建立控制項。  
  
## <a name="see-also"></a>另請參閱  
 [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：在 Visual Studio 內將結構描述對應至工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  