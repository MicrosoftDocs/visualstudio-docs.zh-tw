---
title: Office 專案中的事件
description: 瞭解每個 Office 專案範本如何產生數個事件處理常式，以及這些事件處理常式與 VSTO 增益集的事件處理常式稍有不同。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bf4da3f0b2dd9cbab960a779690aa752744cdae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910320"
---
# <a name="events-in-office-projects"></a>Office 專案中的事件
  每個 Office 專案範本會自動產生數個事件處理常式。 文件層級自訂的事件處理常式與 VSTO 增益集的事件處理常式有些許不同。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>檔層級專案
 Visual Studio 會在文件層級自訂中為新的或現有的文件或工作表，提供產生的後置程式碼。 這個程式碼會引發兩個不同的事件： **Startup** 和 **Shutdown**。

### <a name="startup-event"></a>Startup 事件
 在執行文件且組件中的所有初始設定程式碼都已執行之後，每個主項目 (文件、活頁簿或工作表) 都會引發 **Startup** 事件。 這是在程式碼執行的類別建構函式中，所執行的最後動作。 如需主專案的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

 當您建立文件層級專案時，Visual Studio 會在產生的程式碼檔案中建立 **Startup** 事件的事件處理常式：

- 如果是 Microsoft Office Word 專案，則事件處理常式的名稱為 `ThisDocument_Startup`。

- 如果是 Microsoft Office Excel 專案，則事件處理常式有下列名稱：

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown 事件
 當已載入您程式碼的應用程式定義域即將卸載時，每個主項目 (文件或工作表) 都會引發 **Shutdown** 事件。 在卸載時，於類別中呼叫它是最後要執行的動作。

 當您建立文件層級專案時，Visual Studio 會在產生的程式碼檔案中建立 **Shutdown** 事件的事件處理常式：

- 如果是 Microsoft Office Word 專案，則事件處理常式的名稱為 `ThisDocument_Shutdown`。

- 如果是 Microsoft Office Excel 專案，則事件處理常式有下列名稱：

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> 在文件的 **Shutdown** 事件處理常式執行期間，請勿以程式設計方式移除控制項。 當 **Shutdown** 事件發生時，文件的 UI 項目便無法再使用。 如果您想要在應用程式關閉之前移除控制項，請將程式碼加入其他事件處理常式，例如 **BeforeClose** 或 **BeforeSave**。

### <a name="event-handler-method-declarations"></a>事件處理常式方法宣告
 每個事件處理常式方法宣告都具有傳遞給它的相同引數： *sender* 和 *e*。 在 Excel 中， *sender* 引數會參考工作表，例如 `Sheet1` 或 `Sheet2`；在 Word 中， *sender* 引數會參考文件。 *e* 引數會參考事件的標準引數 (在此情況下不會使用)。

 下列程式碼範例會顯示 Word 文件層級專案中的預設事件處理常式。

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 下列程式碼範例會顯示 Excel 文件層級專案中的預設事件處理常式。

> [!NOTE]
> 下列程式碼範例顯示 `Sheet1` 類別中的事件處理常式。 其他主項目類別中的事件處理常式名稱會對應至這個類別名稱。 例如，在 `Sheet2` 類別中， **Startup** 事件處理常式的名稱為 `Sheet2_Startup`。 在 `ThisWorkbook` 類別中， **Startup** 事件處理常式的名稱為 `ThisWorkbook_Startup`。

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>檔層級 Excel 專案中的事件順序
 呼叫 Excel 專案中 **Startup** 事件處理常式的順序如下：

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. 順序中的其他工作表。

   呼叫活頁簿方案中 **Shutdown** 事件處理常式的順序如下：

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. 順序中的其他工作表。

    此順序是在編譯專案時決定。 如果使用者在執行階段重新排列工作表，則下次開啟或關閉活頁簿時，引發事件的順序並不會因而變更。

## <a name="vsto-add-in-projects"></a>VSTO 增益集專案
 Visual Studio 提供 VSTO 增益集產生的程式碼。此程式碼會引發兩個不同的事件： <xref:Microsoft.Office.Tools.AddInBase.Startup> 和 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 。

### <a name="startup-event"></a>Startup 事件
 VSTO 增益集載入並執行組件中的所有初始化程式碼之後，會引發 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件。 這個事件是由所產生程式碼檔中的 `ThisAddIn_Startup` 方法處理。

 `ThisAddIn_Startup` 事件處理常式中的程式碼是第一個執行的使用者程式碼，除非您的增益集會覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 方法。 在這個情況下， `ThisAddIn_Startup` 事件處理常式會在 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>之後呼叫。

 `ThisAdd-In_Startup`如果程式碼需要開啟檔，請勿在事件處理常式中加入程式碼。 相反地，請將程式碼加入 Office 應用程式在使用者建立或開啟文件時所引發的事件。 如需詳細資訊，請參閱 [Office 應用程式啟動時存取檔](../vsto/programming-vsto-add-ins.md#AccessingDocuments)。

 如需 VSTO 增益集啟動順序的詳細資訊，請參閱 [Vsto 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。

### <a name="shutdown-event"></a>Shutdown 事件
 當已載入您程式碼的應用程式定義域即將卸載時，會引發 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 事件。 這個事件是由所產生程式碼檔中的 `ThisAddIn_Shutdown` 方法處理。 卸載 VSTO 增益集時，這個事件處理常式會是最後一個執行的使用者程式碼。

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Outlook VSTO 增益集的關機事件
 只有當使用者藉由使用 Outlook 的 [COM 增益集] 對話方塊停用 VSTO 增益集時，才會引發 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 事件。 Outlook 結束時不會引發此事件。 如果您有必須在 Outlook 結束時執行的程式碼，請處理下列任一事件：

- <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> 物件的 <xref:Microsoft.Office.Interop.Outlook.Application> 事件。

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> 物件的 <xref:Microsoft.Office.Interop.Outlook.Explorer> 事件。

> [!NOTE]
> 您可以修改登錄，強制 Outlook 在結束時引發 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 事件。 不過，如果系統管理員還原此設定，則 Outlook 結束時，便不會再執行任何您加入至 `ThisAddIn_Shutdown` 方法的程式碼。 如需詳細資訊，請參閱 [Outlook 2010 的關機變更](/previous-versions/office/developer/office-2010/ee720183(v=office.14))。

## <a name="see-also"></a>另請參閱
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [Office 專案範本總覽](../vsto/office-project-templates-overview.md)
