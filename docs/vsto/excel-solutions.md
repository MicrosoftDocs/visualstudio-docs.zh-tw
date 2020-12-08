---
title: Excel 方案
description: '瞭解您可以使用專案範本將 Excel 自動化、延伸 Excel 功能，以及自訂 Excel 使用者介面 (UI) '
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6ca4cfd45c1147d10ffaf8d3308b9adb09c689e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848114"
---
# <a name="excel-solutions"></a>Excel 方案
  Visual Studio 提供的專案範本，可用以建立 Microsoft Office Excel 的文件層級自訂和 VSTO 增益集。 您可以使用這些解決方案自動化 Excel、擴充 Excel 功能和自訂 Excel 使用者介面 (UI)。 如需檔層級自訂和 VSTO 增益集之間差異的詳細資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 此主題提供下列資訊：

- [自動化 Excel](#automating)。

- [開發 Excel 的檔層級自訂](#doclevel)。

- [開發 Excel 的 VSTO 增益集](#applevel)。

- [自訂 Excel 的使用者介面](#UI)。

## <a name="automate-excel"></a><a name="automating"></a> 自動化 Excel
 Excel 物件模型會公開您可用來自動化 Excel 的許多類型。 例如，您可以程式設計的方式建立圖表、格式化工作表，以及設定範圍和儲存格的值。 如需詳細資訊，請參閱 [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)。

 在 Visual Studio 中開發 Excel 方案時，您也可以在解決方案中使用 *「主項目」* (host items) 和 *「主控制項」* (host controls)。 這些都是在 Excel 物件模型中擴充某些常用物件的物件，例如 <xref:Microsoft.Office.Interop.Excel.Worksheet> 和 <xref:Microsoft.Office.Interop.Excel.Range> 物件。 這些擴充物件的行為與它們所根據的 Excel 物件一樣，但是這些物件會在物件中加入額外的事件和資料繫結功能。 如需詳細資訊，請參閱 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> 開發 Excel 的檔層級自訂
 Microsoft Office Excel 文件層級自訂是由與特定活頁簿相關聯的組件所組成。 組件通常是透過自訂 UI 及自動化 Excel 來擴充活頁簿。 不同於與 Excel 本身相關聯的 VSTO 增益集，您在自訂中實作的功能只有在 Excel 中開啟相關聯的活頁簿時才能使用。

 若要建立 Excel 的檔層級自訂專案，請在 Visual Studio 的 [ **新增專案** ] 對話方塊中，使用 [excel 活頁簿] 或 [excel 範本] 專案範本。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

 如需檔層級自訂運作方式的詳細資訊，請參閱 [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

### <a name="excel-customization-programming-model"></a>Excel 自訂程式設計模型
 當您建立 Excel 的文件層級專案時，Visual Studio 會產生為解決方案基礎的數個類別： `ThisWorkbook`、 `Sheet1`、 `Sheet2`和 `Sheet3`。 這些類別代表與解決方案相關聯的活頁簿和工作表，並提供撰寫程式碼的起點。

 如需有關您可以在檔層級專案中使用之產生的類別和其他功能的詳細資訊，請參閱 [程式檔層級自訂程式](../vsto/programming-document-level-customizations.md)。

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> 開發 Excel 的 VSTO 增益集
 Microsoft Office Excel 的 VSTO 增益集是由 Excel 載入的組件所組成。 組件通常是透過自訂 UI 及自動化 Excel 來擴充 Excel。 不同于與特定活頁簿相關聯的檔層級自訂，您在 VSTO 增益集中所執行的功能不受限於任何單一活頁簿。

 若要建立 Excel 的 VSTO 增益集專案，請在 Visual Studio 的 [ **新增專案** ] 對話方塊中，使用 [excel 活頁簿] 或 [excel 範本] 專案範本。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

 如需 VSTO 增益集運作方式的一般資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。

### <a name="excel-add-in-programming-model"></a>Excel 增益集程式設計模型
 當您建立 Excel VSTO 增益集專案時，Visual Studio 會產生名為 `ThisAddIn`的類別，這是方案的基礎。 這個類別會提供撰寫程式碼的起點，還會向 VSTO 增益集公開 Excel 物件模型。

 如需 VSTO 增益集中可用之 `ThisAddIn` 類別和其他 Visual Studio 功能的詳細資訊，請參閱 [程式 Vsto 增益集](../vsto/programming-vsto-add-ins.md)。

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> 自訂 Excel 的使用者介面
 有幾種不同的方式可以自訂 Excel 的使用者介面。 有些選項適用於所有專案類型，有些選項則僅限 VSTO 增益集或文件層級自訂使用。

### <a name="options-for-all-project-types"></a>所有專案類型的選項
 下表列出的自訂選項，文件層級自訂和 VSTO 增益集皆可使用。

|Task|取得詳細資訊|
|----------|--------------------------|
|自訂功能區。|[功能區總覽](../vsto/ribbon-overview.md)|
|在文件層級自訂的自訂活頁簿工作表，或任何開啟的 VSTO 增益集活頁簿中，加入 Windows Form 控制項或擴充的 Excel 控制項。|[如何：將 Windows forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [如何：將圖表控制項加入至工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>檔層級自訂的選項
 下表列出的自訂選項僅限文件層級自訂使用。

|Task|取得詳細資訊|
|----------|--------------------------|
|在活頁簿中加入執行窗格。|[動作窗格總覽](../vsto/actions-pane-overview.md)<br /><br /> [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|在工作表中加入對應到 XML 節點的擴充範圍控制項。|[如何：將 XMLMappedRange 控制項加入至工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>VSTO 增益集的選項
 下表列出的自訂選項僅限 VSTO 增益集使用。

|Task|取得詳細資訊|
|----------|--------------------------|
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>相關主題

| 標題 | 描述 |
| - | - |
| [Excel 物件模型總覽](../vsto/excel-object-model-overview.md) | 提供 Excel 物件模型所提供的主要類型的概觀。 |
| [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md) | 提供可以用在 Excel 方案中之擴充物件 (由 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]所提供) 的相關資訊。 |
| [Excel 方案的全球化與當地語系化](../vsto/globalization-and-localization-of-excel-solutions.md) | 包含會在有非英文設定的 Windows 電腦上執行 Excel 方案之特殊考量的相關資訊。 |
| [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md) | 描述如何在 Excel 工作表中加入 Windows Form 控制項。 |
| [逐步解說：建立 Excel 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | 示範如何建立 Excel 的基本文件層級自訂。 |
| [逐步解說：建立 Excel 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | 示範如何建立 Excel 的基本 VSTO 增益集。 |
| [逐步解說：在執行時間于 VSTO 增益集專案中，將控制項加入工作表](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | 示範如何使用 VSTO 增益集，於執行階段在工作表中加入 Windows Form 按鈕、 <xref:Microsoft.Office.Tools.Excel.NamedRange>和 <xref:Microsoft.Office.Tools.Excel.ListObject> 。 |
| [瞭解共同撰寫和增益集](./understanding-coauthoring-and-addins.md) | 說明您可能需要對方案進行的調整，以配合共同工作。 |
| [Office 開發中的 Excel 2010](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | 提供開發 Excel 方案的相關文章和參考文件連結。 非專屬於使用 Visual Studio 的 Office 程式開發。 |
