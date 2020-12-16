---
title: XmlMappedRange 控制項
description: 瞭解 XmlMappedRange 控制項是一個範圍，只有當非重複的架構元素對應到 Microsoft Excel 中的資料格時，才會建立這個範圍。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f3b3fd140787d44cdd8364ce77d5292dfcd83f54
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525892"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange 控制項
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項是一個範圍，只有當非重複的架構專案對應到 Microsoft Office Excel 中的資料格時，才會建立這個範圍。 例如，當 `maxOccurs` 架構元素的屬性等於1時。 在 Visual Studio 建立 XML 對應範圍之後，您可以直接對其進行程式設計，而不需要遍歷 Excel 物件模型。 移除專案對應時，您只能在 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Excel 中刪除控制項。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項支援系結至單一資料欄位， (簡單的資料系結) 。 <xref:Microsoft.Office.Tools.Excel.ListObject>控制項可以支援複雜的資料系結，而且會在重複的架構元素對應到資料格時自動建立。 如需詳細資訊，請參閱 [ListObject 控制項](../vsto/listobject-control.md)。

 使用屬性，將控制項系結 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 至資料來源 <xref:System.Windows.Forms.Control.DataBindings%2A> 。 當 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 加入工作表單資料格時，Visual Studio 會自動從對應資料格的資料產生資料集，並將控制項系結至該資料集。 的預設資料系結屬性 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 為 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> 。

 如果系結資料集中的資料是透過任何機制進行更新，控制項就會 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 反映變更。

## <a name="formatting"></a>格式化
 您可以將相同的格式套用至 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 可套用至的控制項 <xref:Microsoft.Office.Interop.Excel.Range> 。 這包括框線、字型、數字格式和樣式。

## <a name="events"></a>事件
 控制項可用的事件 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 包括：

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>另請參閱
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [如何：將 XMLMappedRange 控制項加入至工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
