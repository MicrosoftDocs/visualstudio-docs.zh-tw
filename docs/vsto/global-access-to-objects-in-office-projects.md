---
title: 全域存取 Office 專案中的物件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6e5b27eaff0b462e257d1d972c5b950cd1f5ab1a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066763"
---
# <a name="global-access-to-objects-in-office-projects"></a>全域存取 Office 專案中的物件
  當您建立 Office 專案時，Visual Studio 會在專案中自動產生名為 `Globals` 的類別。 您可以使用 `Globals` 類別，在執行階段從專案的任何程式碼存取數個不同的專案項目。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>如何使用 Globals 類別
 `Globals` 是靜態類別，會將某些項目的參考保留在專案中。 您可以使用 `Globals` 類別，在執行階段從專案的任何程式碼存取下列項目：

- Excel 活頁簿或範本專案中的 `ThisWorkbook` 和 `Sheet`*n* 類別。 您可以使用 `Globals.ThisWorkbook` 和 `Sheet`*n* 屬性來存取這些物件。

- Word 文件或範本專案中的 `ThisDocument` 類別。 您可以使用 `Globals.ThisDocument` 屬性來存取這個物件。

- `ThisAddIn` VSTO 增益集專案中的類別。 您可以使用 `Globals.ThisAddIn` 屬性來存取這個物件。

- 專案中使用 [功能區設計工具] 自訂的所有功能區。 您可以使用 `Globals.Ribbons` 屬性來存取功能區。 如需詳細資訊，請參閱 <<c0> [ 存取在執行階段功能區](../vsto/accessing-the-ribbon-at-run-time.md)。

- Outlook VSTO 增益集專案中的所有 Outlook 表單區域。 您可以使用 `Globals.FormRegions` 屬性來存取表單區域。 如需詳細資訊，請參閱 <<c0> [ 存取表單區域在執行階段](../vsto/accessing-a-form-region-at-run-time.md)。

- Factory 物件，可讓您在執行階段於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]目標專案中建立功能區控制項和主項目。 您可以使用 `Globals.Factory` 屬性來存取這個物件。 這個物件是可實作下列其中一個介面的類別執行個體：

  - <xref:Microsoft.Office.Tools.Factory>

  - <xref:Microsoft.Office.Tools.Excel.Factory>

  - <xref:Microsoft.Office.Tools.Outlook.Factory>

  - <xref:Microsoft.Office.Tools.Word.Factory>

  例如，您可以使用 `Globals.Sheet1` 屬性在使用者按一下 Excel 文件層級專案中執行窗格上的按鈕時，將文字插入 <xref:Microsoft.Office.Tools.Excel.NamedRange> 上的 `Sheet1` 控制項。

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

## <a name="initialize-the-globals-class"></a>初始化 Globals 類別
 嘗試使用的程式碼`Globals`類別的文件或 VSTO 增益集初始化之前可能會擲回執行的階段例外狀況。 例如，在宣告類別層級變數時使用 `Globals` 可能會失敗，因為 `Globals` 類別可能不會在宣告的物件具現化之前，使用所有主項目的參考進行初始化。

> [!NOTE]
>  雖然 `Globals` 類別絕對不會在設計階段初始化，但是設計工具卻會建立控制項執行個體。 這表示，如果您建立使用者控制項所使用的屬性`Globals`類別從使用者控制項類別中，您必須檢查屬性是否會傳回**null**您嘗試使用傳回的物件之前。

## <a name="see-also"></a>另請參閱
- [在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)
- [存取表單區域在執行階段](../vsto/accessing-a-form-region-at-run-time.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [文件主項目](../vsto/document-host-item.md)
- [Workbook 主項目](../vsto/workbook-host-item.md)
- [工作表主項目](../vsto/worksheet-host-item.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
