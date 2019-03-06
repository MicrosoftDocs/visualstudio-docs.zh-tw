---
title: 使用擴充的物件自動化 Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03ea220bf886352a05cc67bdd44a9504dcd86964
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600850"
---
# <a name="automate-excel-by-using-extended-objects"></a>使用擴充的物件自動化 Excel
  在 Visual Studio 中開發 Excel 方案時，您可以在方案中使用 *「主項目」* (host items) 和 *「主控制項」*(host controls)。 這些物件可以擴充 Excel 物件模型 (也就是 Excel 的主要 Interop 組件公開的物件模型) 中某些常用的物件，例如 <xref:Microsoft.Office.Interop.Excel.Worksheet> 和 <xref:Microsoft.Office.Interop.Excel.Range> 物件。 這些擴充物件的行為與它們所根據的 Excel 物件一樣，但是這些物件會將額外的功能 (例如新事件和資料繫結功能) 加入物件中 。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 VSTO 增益集和文件層級自訂中都提供主項目和主控制項，不過針對每種方案類型來說，可在其中使用主項目和主控制項的內容會有所不同。 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

## <a name="excel-host-items"></a>Excel 主項目
 Excel 專案可讓您存取數個主項目：

-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. 包含這個主項目，並代表您的專案中的工作表。 它還可當成 Managed 控制項 (包括主控制項與 Windows Form 控制項) 的容器使用，而且會在其介面維護控制項的相關資訊。 如需詳細資訊，請參閱 <<c0> [ 工作表主項目](../vsto/worksheet-host-item.md)。

-   <xref:Microsoft.Office.Tools.Excel.Workbook>. 這個主項目表示專案中的活頁簿，可當做活頁簿中所有工作表共用之元件的容器。 如需詳細資訊，請參閱 < [Workbook 主項目](../vsto/workbook-host-item.md)。

-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. 這個主項目表示 Excel 中的工作表，其只包含一個圖表並會公開事件。

     在設計階段將圖表工作表當做新工作表加入 Microsoft Office Excel 文件層級自訂專案時，Visual Studio 會自動建立 <xref:Microsoft.Office.Tools.Excel.ChartSheet> 主項目。

     雖然 <xref:Microsoft.Office.Tools.Excel.ChartSheet> 主項目是 Excel 中的工作表，但是您不可以將任何控制項加入該圖表。 如果您想要在含有圖表的工作表上加入其他控制項，請勿使用圖表工作表。 您可以改為使用 <xref:Microsoft.Office.Tools.Excel.Chart> 主控制項，將圖表做為內嵌物件放置在工作表上。 如需詳細資訊，請參閱 <<c0> [ 圖表控制項](../vsto/chart-control.md)。

## <a name="excel-host-controls"></a>Excel 主控制項
 有數個 Excel 主控制項可以協助您建立、組織與自動化活頁簿和工作表。 這些主控制項能夠提供其原生 Excel 物件模型對等用法所無法提供的事件與資料繫結功能。

 如需可用於 Excel 專案中之主控制項的詳細資訊，請參閱下列主題：

-   [圖表控制項](../vsto/chart-control.md)

-   [ListObject 控制項](../vsto/listobject-control.md)

-   [NamedRange 控制項](../vsto/namedrange-control.md)

-   [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>另請參閱
- [如何：使用資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)
- [如何：將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [如何：將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [如何：將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [如何：將 XMLMappedRange 控制項加入工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
- [如何：調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)
- [如何：新的資料列加入 ListObject 控制項時驗證資料](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)
- [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
