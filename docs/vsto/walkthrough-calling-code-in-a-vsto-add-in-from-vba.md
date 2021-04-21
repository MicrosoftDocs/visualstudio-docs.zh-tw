---
title: 逐步解說：從 VBA 呼叫 VSTO 增益集中的程式碼
description: 瞭解如何將 VSTO 增益集中的物件公開給其他 Microsoft Office 方案，包括 Visual Basic for Applications (VBA) 和 COM VSTO 增益集。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824597"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>逐步解說：從 VBA 呼叫 VSTO 增益集中的程式碼
  本逐步解說示範如何將 VSTO 增益集中的物件公開給其他 Microsoft Office 方案，包含 Visual Basic for Applications (VBA) 和 COM VSTO 增益集。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 雖然本逐步解說特別使用 Excel，但是所示範的概念卻同樣適用於 Visual Studio 所提供的任何 VSTO 增益集專案範本。

 本逐步解說將說明下列工作：

- 定義可以公開給其他 Office 方案的類別。

- 將類別公開給其他 Office 方案。

- 從 VBA 程式碼呼叫類別的方法。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>建立 VSTO 增益集專案
 第一步是建立 Excel 的 VSTO 增益集專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 Excel VSTO 增益集專案範本建立名為 **ExcelImportData** 的 Excel VSTO 增益集專案。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔，並將 [ExcelImportData]  專案加入 [方案總管] 。

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>定義可以公開給其他 Office 方案的類別
 本逐步解說的目的是為了從 VBA 程式碼在您的 VSTO 增益集中呼叫 `ImportData` 類別的 `AddInUtilities` 方法。 這個方法會將字串寫入至使用中工作表的儲存格 A1。

 若要將 `AddInUtilities` 類別公開給其他 Office 方案，您必須使該類別成為公用類別，且為 COM 可見。 您也必須公開類別中的 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 介面。 下列程序中的程式碼會示範符合這些需求的其中一種方式。 如需詳細資訊，請參閱 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)。

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>定義可以公開給其他 Office 方案的類別

1. 在 [專案]  功能表上，按一下 [加入類別] 。

2. 在 [加入新項目]  對話方塊中，將新類別的名稱變更為 **AddInUtilities**，然後按一下 [加入] 。

     **AddInUtilities.cs** 或 **AddInUtilities.vb** 檔案隨即在 [程式碼編輯器] 中開啟。

3. 將下列指示詞新增至檔案頂端。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. 使用下列程式碼取代 `AddInUtilities` 類別。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     這個程式碼讓 `AddInUtilities` 類別為 COM 可見，並將 `ImportData` 方法加入這個類別。 為了公開 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 介面， `AddInUtilities` 類別也會具有 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性，並實作為 COM 可見的介面。

## <a name="expose-the-class-to-other-office-solutions"></a>將類別公開給其他 Office 方案
 若要將 `AddInUtilities` 類別公開給其他 Office 方案，請覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 類別中的 `ThisAddIn` 方法。 在您的覆寫中，傳回 `AddInUtilities` 類別的執行個體。

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>將 AddInUtilities 類別公開給其他 Office 方案

1. 展開 [方案總管] 中的 [Excel] 。

2. 以滑鼠右鍵按一下 **ThisAddIn.cs** 或 **ThisAddIn.vb**，然後按一下 [檢視程式碼]。 

3. 將下列程式碼新增至 `ThisAddIn` 類別。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. 在 [建置] 功能表上，按一下 [建置方案]。

     確認方案建置無誤。

## <a name="test-the-vsto-add-in"></a>測試 VSTO 增益集
 您可以從多種不同類型的 Office 方案呼叫 `AddInUtilities` 類別。 在本逐步解說中，您會在 Excel 活頁簿中使用 VBA 程式碼。 如需您也可以使用之其他 Office 方案類型的詳細資訊，請參閱 [從其他 office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)的程式碼。

### <a name="to-test-your-vsto-add-in"></a>測試 VSTO 增益集

1. 按 **F5** 執行您的專案。

2. 在 Excel 中，將現用活頁簿儲存為「Excel 啟用巨集的活頁簿」 (*.xlsm)。 將它儲存在方便取用的位置，例如桌面。

3. 按一下 [功能區] 上的 [開發人員]  索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [程式碼]  群組中，按一下 [Visual Basic] 。

     [Visual Basic 編輯器] 隨即開啟。

5. 按兩下 [專案]  視窗中的 [ThisWorkbook] 。

     `ThisWorkbook` 物件的程式碼檔隨即開啟。

6. 將下列 VBA 程式碼加入程式碼檔案。 此程式碼會先取得代表 **ExcelImportData** VSTO 增益集的 microsoft.office.core.comaddin.object 物件。 然後，程式碼會使用 Microsoft.office.core.comaddin.object 物件的 Object 屬性來呼叫 `ImportData` 方法。

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. 按 **F5**。

8. 請確認新的 **Imported Data** 工作表是否已加入至活頁簿。 此外，請確認儲存格 A1 是否包含字串 **This is my data**。

9. 結束 Excel。

## <a name="next-steps"></a>下一步
 您可以從下列主題進一步了解 VSTO 增益集的程式設計：

- 使用 `ThisAddIn` 類別來自動化主應用程式，並執行 VSTO 增益集專案中的其他工作。 如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

- 在 VSTO 增益集中建立自訂工作窗格。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md) 與 [如何：將自訂工作窗格加入至應用程式](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。

- 在 VSTO 增益集中自訂功能區。 如需詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md) 和 how [to：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。

## <a name="see-also"></a>另請參閱
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
