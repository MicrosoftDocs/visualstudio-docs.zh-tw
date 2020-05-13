---
title: Excel 物件模型概述
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649418"
---
# <a name="excel-object-model-overview"></a>Excel 物件模型概述
  若要開發使用 Microsoft Office Excel 的方案，您可以與 Excel 物件模型提供的物件進行互動。 本主題將介紹最重要的物件：

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  這個物件模型密切遵循其使用者介面。 <xref:Microsoft.Office.Interop.Excel.Application> 物件代表整個應用程式，而每個 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件都包含 `Worksheet` 物件的集合。 其中，代表儲存格的主要抽象物件是 <xref:Microsoft.Office.Interop.Excel.Range> 物件，它可以讓您使用個別儲存格或儲存格群組。

  除了 Excel 物件模型外,Visual Studio 中的 Office 專案還提供擴展 Excel 物件模型中某些物件的*主機項*和*主機控制件*。 主項目和主控制項的行為與它們所擴充的 Excel 物件相同，但還具有其他功能 (例如資料繫結功能和額外事件)。 有關詳細資訊,請參閱使用擴展物件和[主機項和主機控件概述](../vsto/host-items-and-host-controls-overview.md)[的「自動 Excel」。。](../vsto/automating-excel-by-using-extended-objects.md)

  本主題提供 Excel 物件模型的簡短概觀。 有關可以瞭解有關整個 Excel 物件模型詳細資訊的資源,請參閱使用[Excel 物件模型文件](#ExcelOMDocumentation)。

## <a name="access-objects-in-an-excel-project"></a>存取 Excel 專案中的物件
 當您為 Excel 建立新的 VSTO 外接程式專案時,Visual Studio 會自動建立*ThisAddIn.vb*或*ThisAddIn.cs*代碼檔。 您可以使用 `Me.Application` 或 `this.Application`，來存取 Application 物件。

 當您建立 Excel 的新文件層級專案時，可以選擇建立新的 Excel 活頁簿或 Excel 範本專案。 Visual Studio 會在新的 Excel 專案中，自動為活頁簿和範本專案建立下列程式碼檔。

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 您可以在專案中使用 `Globals` 類別，從個別的類別之外存取 `ThisWorkbook`、`Sheet1`、`Sheet2` 或 `Sheet3`。 有關詳細資訊,請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。 下面的範例呼叫方法<xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>,`Sheet1`無論程式碼是`Sheet`放置在*n*類別的`ThisWorkbook`一個類別 。

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 由於 Excel 文件包含高度結構化的資料，因此物件模型不僅層級分明，而且非常明確。 Excel 提供了數百個物件,您可能希望與之交互,但您可以通過關注可用物件的一小部分來在物件模型上找到良好的開端。 這些物件包含下列四個項目：

- Application

- 活頁簿

- 工作表

- 範圍

  使用 Excel 執行的大部分工作都是以這四個物件及其成員為中心。

### <a name="application-object"></a>應用程式物件
 Excel <xref:Microsoft.Office.Interop.Excel.Application> 物件代表 Excel 應用程式本身。 <xref:Microsoft.Office.Interop.Excel.Application> 物件會公開有關執行中應用程式、套用至該執行個體的選項，以及目前在執行個體中開啟之使用者物件的大量資訊。

> [!NOTE]
> 請勿在 Excel 中，將 <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> 物件的 <xref:Microsoft.Office.Interop.Excel.Application> 屬性設定為 **false**(Native Office Object)。 將這個屬性設定為 false，會導致 Excel 無法引發任何事件，包括主控制項的事件在內。

### <a name="workbook-object"></a>工作簿物件
 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件代表 Excel 應用程式中的單一活頁簿。

 Visual Studio 中的 Office 程式開發工具會藉由提供 <xref:Microsoft.Office.Interop.Excel.Workbook> 類型，來擴充 <xref:Microsoft.Office.Tools.Excel.Workbook> 物件。 這個類型可讓您存取 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件的所有功能。 有關詳細資訊,請參閱[工作簿主機項](../vsto/workbook-host-item.md)。

### <a name="worksheet-object"></a>Worksheet 物件
 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件是 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合的成員。 <xref:Microsoft.Office.Interop.Excel.Worksheet> 的許多屬性、方法和事件都與 <xref:Microsoft.Office.Interop.Excel.Application> 或 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件所提供的成員完全相同或類似。

 Excel 提供 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合，做為 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件的屬性。 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的每個成員都是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.Chart> 物件。

 Visual Studio 中的 Office 程式開發工具會藉由提供 <xref:Microsoft.Office.Interop.Excel.Worksheet> 類型，來擴充 <xref:Microsoft.Office.Tools.Excel.Worksheet> 物件。 這個類型可讓您存取 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件的所有功能，以及新功能 (例如可以裝載 Managed 控制項和處理新事件)。 有關詳細資訊,請參閱[工作表主機項](../vsto/worksheet-host-item.md)。

### <a name="range-object"></a>Range 物件
 <xref:Microsoft.Office.Interop.Excel.Range> 物件是您在 Excel 應用程式中最常使用的物件。 若要操作 Excel 中的任何區域，您必須先將其表示為 <xref:Microsoft.Office.Interop.Excel.Range> 物件，然後再搭配該範圍的方法和屬性使用。 <xref:Microsoft.Office.Interop.Excel.Range> 物件代表一個儲存格、一個資料列、一個資料行、含有一或多個不一定連續之儲存格區塊的儲存格選取範圍，或甚至是多個工作表上的儲存格群組。

 Visual Studio 會藉由提供 <xref:Microsoft.Office.Tools.Excel.NamedRange> 和 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 類型，來擴充 <xref:Microsoft.Office.Interop.Excel.Range> 物件。 這些類型具有與 <xref:Microsoft.Office.Interop.Excel.Range> 物件相同的大部分功能，以及新功能 (例如資料繫結功能和新事件)。 有關詳細資訊,請參閱[命名Range控制項](../vsto/namedrange-control.md)和[XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)。

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>使用 Excel 物件模型文件
 如需 Excel 物件模型的完整資訊，您可以參閱 Excel 主要 Interop 組件 (PIA) 參考和 VBA 物件模型參考。

### <a name="primary-interop-assembly-reference"></a>主互操作程式集引用
 Excel PIA 參考文件說明 Excel 主要 Interop 組件中的類型。 此文件可從以下位置獲得[:Excel 2010 主互操作程式集參考](office-primary-interop-assemblies.md)。

 有關 Excel PIA 設計的詳細資訊,例如 PIA 中的類別和介面之間的差異以及 PIA 中事件是如何實現的,請參閱[Office 主互通程式集中的類和介面概述](/previous-versions/office/office-12/ms247299(v=office.12))。

### <a name="vba-object-model-reference"></a>VBA 物件模型引用
 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的 Excel 物件模型。 有關詳細資訊,請參閱[Excel 2010 物件模型參考](/office/vba/api/overview/Excel/object-model)。

 VBA 物件模型參考中的所有物件和成員都會對應至 Excel PIA 中的類型和成員。 例如,VBA 物件模型引用中的工作表對象對應於 Excel PIA<xref:Microsoft.Office.Interop.Excel.Worksheet>中的物件。 雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Excel 專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯為 Visual Basic 或 Visual C#。

### <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[Excel 解決方案](../vsto/excel-solutions.md)|說明如何建立 Microsoft Office Excel 的文件層級自訂和 VSTO 增益集。|
|[使用範圍](../vsto/working-with-ranges.md)|提供示範如何使用範圍執行常見工作的範例。|
|[使用工作表](../vsto/working-with-worksheets.md)|提供示範如何使用工作表執行常見工作的範例。|
|[使用工作簿](../vsto/working-with-workbooks.md)|提供示範如何使用活頁簿執行常見工作的範例。|
