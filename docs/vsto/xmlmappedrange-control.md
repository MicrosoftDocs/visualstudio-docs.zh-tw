---
title: XmlMappedRange 控制項
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985366"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 控制項
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項是一種範圍，只有在非重複的架構專案對應到 Microsoft Office Excel 中的資料格時，才會建立這個範圍。 例如，當 schema 元素的 `maxOccurs` 屬性等於1時。 在 Visual Studio 建立 XML 對應範圍之後，您可以直接對其進行程式設計，而不需要遍歷 Excel 物件模型。 移除專案對應時，您只能在 Excel 中刪除 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項支援系結至單一資料欄位（簡單的資料系結）。 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項可以支援複雜的資料系結，而且會在重複的架構元素對應到資料格時自動建立。 如需詳細資訊，請參閱[ListObject control](../vsto/listobject-control.md)。

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項會使用 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性系結至資料來源。 當 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 加入至工作表資料格時，Visual Studio 會自動從對應儲存格中的資料產生資料集，並將控制項系結至該資料集。 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 的預設資料系結屬性是 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>。

 如果系結資料集中的資料是透過任何機制更新，<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項就會反映變更。

## <a name="formatting"></a>格式化
 您可以將相同的格式套用至 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項，讓您可以將它套用至 <xref:Microsoft.Office.Interop.Excel.Range>。 這包括框線、字型、數字格式和樣式。

## <a name="events"></a>「事件」
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項可用的事件如下：

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>請參閱
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [如何：將 XMLMappedRange 控制項加入至工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
