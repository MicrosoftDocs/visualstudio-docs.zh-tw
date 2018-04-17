---
title: XmlMappedRange 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1bc4516f0ca14427e5e63a40ae58ddd60436dfd6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 控制項
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項為非重複結構描述元素會對應到 Microsoft Office Excel 中的資料格時，才會建立一個範圍。 例如，當`maxOccurs`屬性結構描述元素等於 1。 Visual Studio 會建立對應的 XML 範圍之後，您可以針對它程式直接而不必周遊 Excel 物件模型。 您只能刪除<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>內時就會移除項目對應的 Excel 控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 使用 XML 中的對應 Excel？](http://go.microsoft.com/fwlink/?LinkID=130288)。  
  
## <a name="binding-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項支援繫結至單一資料欄位 （簡單資料繫結）。 <xref:Microsoft.Office.Tools.Excel.ListObject>控制項可以支援複雜資料繫結，而且重複的結構描述元素會對應至資料格中時自動建立。 如需詳細資訊，請參閱 [ListObject Control](../vsto/listobject-control.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項繫結至資料來源使用<xref:System.Windows.Forms.Control.DataBindings%2A>屬性。 當<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Visual Studio 自動產生資料集從中對應的儲存格的資料，並將控制項繫結至該資料集加入至工作表儲存格。 預設資料繫結屬性<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>是<xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>。  
  
 如果透過任何機制，更新繫結資料集中的資料<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項會反映這些變更。  
  
## <a name="formatting"></a>格式化  
 您可以套用相同的格式設定<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項，您可以套用到<xref:Microsoft.Office.Interop.Excel.Range>。 這包括框線、字型、數字格式和樣式。  
  
## <a name="events"></a>事件  
 事件可供<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>的項目：  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>另請參閱  
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何： 將 XMLMappedRange 控制項加入工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 將結構描述對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  