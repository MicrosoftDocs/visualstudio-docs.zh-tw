---
title: '逐步解說：在 Visual c # 專案中呼叫 VBA 的程式碼'
description: 瞭解如何從活頁簿中的 Visual Basic for Applications (VBA) 程式碼，呼叫 Microsoft Excel 檔層級自訂中的方法。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 260872096f36f91a2618f636e297d3c48b3fe51b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824467"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>逐步解說：在 Visual c # 專案中呼叫 VBA 的程式碼
  本逐步解說示範如何從活頁簿中的 Visual Basic for Applications (VBA) 程式碼，呼叫 Microsoft Office Excel 文件層級自訂中的方法。 這個程序和三個基本步驟相關：將方法加入 `Sheet1` 主項目類別、將方法公開至活頁簿中的 VBA 程式碼，然後從活頁簿中的 VBA 程式碼呼叫此方法。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 雖然這個逐步解說特地使用 Excel，但本逐步解說所示範的概念同樣適用於 Word 的文件層級專案。

 本逐步解說將說明下列工作：

- 建立含有 VBA 程式碼的活頁簿。

- 使用 Excel 的信任中心來信任活頁簿的位置。

- 將方法加入 `Sheet1` 主項目類別。

- 擷取 `Sheet1` 主項目類別的介面。

- 將方法公開至 VBA 程式碼。

- 從 VBA 程式碼呼叫方法。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>建立包含 VBA 程式碼的活頁簿
 第一個步驟是建立已啟用巨集的活頁簿，該活頁簿包含簡單 VBA 巨集。 活頁簿必須已含有 VBA 程式碼，您才能將自訂中的程式碼公開至 VBA。 否則，Visual Studio 無法修改 VBA 專案，讓 VBA 程式碼能夠呼叫自訂組件。

 如果您已經有包含想使用之 VBA 程式碼的活頁簿，則可略過這個步驟。

### <a name="to-create-a-workbook-that-contains-vba-code"></a>建立含有 VBA 程式碼的活頁簿

1. 啟動 Excel。

2. 將使用中的檔儲存為 **Excel Macro-Enabled 活頁簿 (\* . xlsm)** 的名稱為 **WorkbookWithVBA**。 將它儲存至方便取用的位置，例如桌面。

3. 按一下 [功能區] 上的 [開發人員]  索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [程式碼]  群組中，按一下 [Visual Basic] 。

     [Visual Basic 編輯器] 隨即開啟。

5. 按兩下 [專案]  視窗中的 [ThisWorkbook] 。

     `ThisWorkbook` 物件的程式碼檔隨即開啟。

6. 將下列 VBA 程式碼加入程式碼檔案。 此程式碼會定義毫無作用的簡單函式。 這個函式的唯一目的在於確保 VBA 專案存在於活頁簿中。 本逐步解說中的後續步驟需要用到此函式。

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. 儲存文件並結束 Excel。

## <a name="create-the-project"></a>建立專案
 您現在即可建立 Excel 的文件層級專案，而該專案會使用您先前建立且已啟用巨集的活頁簿。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 在範本窗格中，展開 [Visual C#] ，然後展開 [Office/SharePoint] 。

4. 選取 [Office 增益集]  節點。

5. 在專案範本清單中，選取 [Excel 2010 活頁簿]  或 [Excel 2013 活頁簿]  專案。

6. 在 [名稱]  方塊中，輸入 **CallingCodeFromVBA**。

7. 按一下 [確定]  。

     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

8. 選取 [複製現有文件] ，然後在 [現有文件的完整路徑]  方塊中，指定您先前建立之 **WorkbookWithVBA** 活頁簿的位置。 如果您使用已啟用巨集的自有活頁簿，則改為指定該活頁簿的位置。

9. 按一下 [完成] 。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在設計工具中開啟 **WorkbookWithVBA** 活頁簿，並將 [CallingCodeFromVBA]  專案加入 [方案總管] 。

## <a name="trust-the-location-of-the-workbook"></a>信任活頁簿的位置
 您必須先信任活頁簿中要執行的 VBA，才能將方案中的程式碼公開至活頁簿中的 VBA 程式碼。 有數種方法能完成這項操作。 在本逐步解說中，您會藉由在 Excel 的 [信任中心]  中信任活頁簿的位置來完成這項工作。

### <a name="to-trust-the-location-of-the-workbook"></a>信任活頁簿的位置

1. 啟動 Excel。

2. 按一下 [檔案]  索引標籤。

3. 按一下 [Excel 選項]  按鈕。

4. 在分類窗格中，按一下 [信任中心] 。

5. 在詳細資料窗格中，按一下 [信任中心設定] 。

6. 在分類窗格中，按一下 [信任位置] 。

7. 在詳細資料窗格中，按一下 [新增位置] 。

8. 在 [Microsoft Office 信任位置]  對話方塊中，瀏覽至包含 [CallingCodeFromVBA]  專案的資料夾。

9. 選取 [同時信任此位置的子資料夾] 。

10. 按一下 [Microsoft Office 信任位置]  對話方塊中的 [確定] 。

11. 按一下 [信任中心]  對話方塊中的 [確定] 。

12. 按一下 [Excel 選項]  對話方塊中的 [確定] 。

13. 結束 **Excel**。

## <a name="add-a-method-to-the-sheet1-class"></a>將方法加入 Sheet1 類別
 目前已設定 VBA 專案，請將公用方法加入您可以從 VBA 程式碼呼叫的 `Sheet1` 主項目類別。

### <a name="to-add-a-method-to-the-sheet1-class"></a>將方法加入 Sheet1 類別

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [Sheet1.cs] ，然後按一下 [檢視程式碼] 。

     **Sheet1.cs** 檔案隨即在 [程式碼編輯器] 中開啟。

2. 將下列程式碼新增至 `Sheet1` 類別。 `CreateVstoNamedRange` 方法會建立位於指定範圍的新 <xref:Microsoft.Office.Tools.Excel.NamedRange> 物件。 這個方法還會建立 <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> 之 <xref:Microsoft.Office.Tools.Excel.NamedRange>事件的事件處理常式。 稍後在本逐步解說中，您會從本文件中的 VBA 程式碼呼叫 `CreateVstoNamedRange` 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet2":::

3. 將下列方法新增至 `Sheet1` 類別。 這個方法會覆寫 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> 方法，以傳回 `Sheet1` 類別目前的執行個體。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet3":::

4. 將下列屬性套用於 `Sheet1` 類別宣告的第一行之前。 這些屬性可以讓 COM 看到類別，但是不會產生類別介面。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet1":::

## <a name="extract-an-interface-for-the-sheet1-class"></a>將 Sheet1 類別的介面解壓縮
 您必須先建立用以定義此方法的公用介面，且必須將此介面公開至 COM，才能將 `CreateVstoNamedRange` 方法公開至 VBA 程式碼。

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>擷取 Sheet1 類別的介面

1. 在 **Sheet1.cs** 程式碼檔案中，按一下 `Sheet1` 類別中的任意處。

2. 按一下 [重構]  功能表上的 [擷取介面] 。

3. 在 [擷取介面]  對話方塊的 [選取 Public 成員以形成介面]  方塊中，按一下 `CreateVstoNamedRange` 方法的項目。

4. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會產生名稱為 `ISheet1`的新介面，而且會修改 `Sheet1` 類別的定義，以便實作 `ISheet1` 介面。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 也會在 [程式碼編輯器] 中開啟 **ISheet1.cs** 檔案。

5. 在 **ISheet1.cs** 檔案中，請以下列程式碼取代 `ISheet1` 介面宣告。 此程式碼會使 `ISheet1` 介面變成公用，並套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性，而讓 COM 看得見介面。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs" id="Snippet4":::

6. 建置專案。

## <a name="expose-the-method-to-vba-code"></a>將方法公開至 VBA 程式碼
 若要將 `CreateVstoNamedRange` 方法公開至活頁簿中的 VBA 程式碼，請將 **主項目的** ReferenceAssemblyFromVbaProject `Sheet1` 屬性設定為 [True] 。

### <a name="to-expose-the-method-to-vba-code"></a>將方法公開至 VBA 程式碼

1. 按兩下 [方案總管] 中的 **Sheet1.cs**。

     **WorkbookWithVBA** 檔案隨即在設計工具中開啟，並顯示 Sheet1。

2. 在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。

3. 按一下訊息中顯示的 [確定]  。

4. 建置專案。

## <a name="call-the-method-from-vba-code"></a>從 VBA 程式碼呼叫方法
 您現在可以從活頁簿中的 VBA 程式碼呼叫 `CreateVstoNamedRange` 方法。

> [!NOTE]
> 在這個逐步解說中，您會在偵錯專案時將 VBA 程式碼加入活頁簿。 您加入此文件的 VBA 程式碼將會在下一次建置專案時被覆寫，因為 Visual Studio 會將組建輸出資料夾中的文件取代為來自主要專案資料夾的文件複本。 如果您要儲存 VBA 程式碼，可以將它複製到專案資料夾的文件中。 如需詳細資訊，請參閱 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

### <a name="to-call-the-method-from-vba-code"></a>從 VBA 程式碼呼叫方法

1. 按 **F5** 執行您的專案。

2. 在 [開發人員]  索引標籤上的 [程式碼]  群組中，按一下 [Visual Basic] 。

     [Visual Basic 編輯器] 隨即開啟。

3. 按一下 [插入]  功能表上的 [模組] 。

4. 將下列程式碼加入新模組。

     這段程式碼會呼叫自訂組件中的 `CreateTable` 方法。 巨集會使用全域 `GetManagedClass` 方法來存取此方法，以存取您公開至 VBA 程式碼的 `Sheet1` 主項目類別。 當您稍早在本逐步解說中設定 `GetManagedClass` ReferenceAssemblyFromVbaProject **屬性時，便已自動產生** 方法。

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. 按 **F5**。

6. 在開啟的活頁簿中，按一下 [Sheet1]  上的儲存格 [A1] 。 確認訊息方塊是否出現。

7. 結束 Excel 但不儲存變更。

## <a name="next-steps"></a>下一步
 您可以在這些主題中，進一步了解如何從 VBA 呼叫 Office 方案中的程式碼：

- 從 VBA 呼叫 Visual Basic 自訂之主項目中的程式碼。 此處理序與 Visual C# 處理序不同。 如需詳細資訊，請參閱 [逐步解說：從 Visual Basic 專案中的 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。

- 從 VBA 呼叫 VSTO 增益集中的程式碼。 如需詳細資訊，請參閱 [逐步解說：從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。

## <a name="see-also"></a>另請參閱
- [合併 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [如何：將程式碼公開給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [如何：將程式碼公開給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
