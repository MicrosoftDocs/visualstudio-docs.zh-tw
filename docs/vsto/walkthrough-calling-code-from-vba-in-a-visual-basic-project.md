---
title: 逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼
description: 瞭解如何從檔中的 Visual Basic for Applications (VBA) 程式碼，呼叫 Microsoft Word 檔層級自訂中的方法。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6016dbf53413f6e55c88edfe930af677472bdaf5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527381"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼
  本逐步解說示範如何從文件中的 Visual Basic for Applications (VBA) 程式碼，呼叫 Microsoft Office Word 文件層級自訂中的方法。 這個程序和三個基本步驟相關：將方法加入 `ThisDocument` 主項目類別、將方法公開至 VBA 程式碼，然後從文件中的 VBA 程式碼呼叫此方法。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 雖然這個逐步解說特地使用 Word，但本逐步解說所示範的概念同樣適用於 Excel 的文件層級專案。

 本逐步解說將說明下列工作：

- 建立包含 VBA 程式碼的文件。

- 使用 Word 的信任中心來信任文件的位置。

- 將方法加入 `ThisDocument` 主項目類別。

- 將方法公開至 VBA 程式碼。

- 從 VBA 程式碼呼叫方法。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>建立包含 VBA 程式碼的檔
 第一個步驟是建立已啟用巨集的文件，該文件包含簡單 VBA 巨集。 文件必須先包含 VBA 專案，您才能根據該文件建立 Visual Studio 專案。 否則，Visual Studio 無法修改 VBA 專案，讓 VBA 程式碼能夠呼叫自訂組件。

 如果您已經有包含想使用之 VBA 程式碼的文件，則可略過這個步驟。

### <a name="to-create-a-document-that-contains-vba-code"></a>建立包含 VBA 程式碼的文件

1. 啟動 Word。

2. 將使用中的檔儲存為 **啟用巨集 Word 檔 (\* docm)** 名稱為 **DocumentWithVBA**。 將它儲存在方便取用的位置，例如桌面。

3. 按一下 [功能區] 上的 [開發人員]  索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [程式碼]  群組中，按一下 [Visual Basic] 。

     [Visual Basic 編輯器] 隨即開啟。

5. 按兩下 [專案]  視窗中的 [ThisDocument] 。

     `ThisDocument` 物件的程式碼檔隨即開啟。

6. 將下列 VBA 程式碼加入程式碼檔案。 此程式碼會定義毫無作用的簡單函式。 這個函式的唯一目的在於確保 VBA 專案存在於文件中。 本逐步解說中的後續步驟需要用到此函式。

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. 儲存文件並結束 Word。

## <a name="create-the-project"></a>建立專案
 您現在即可建立 Word 之文件層級專案，而該專案會使用您先前建立且已啟用巨集的文件。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。 如果您的 IDE 設定為使用 Visual Basic 開發設定，請按一下 [檔案]  功能表上的 [新增專案] 。

3. 在範本窗格中，展開 [Visual Basic] ，然後展開 [Office/SharePoint] 。

4. 選取 [Office 增益集]  節點。

5. 在專案範本清單中，選取 [Word 2010 文件]  或 [Word 2013 文件]  專案。

6. 在 [名稱]  方塊中，輸入 **CallingCodeFromVBA**。

7. 按一下 [確定]。

     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

8. 選取 [複製現有文件] ，然後在 [現有文件的完整路徑]  方塊中，指定您先前建立之 **DocumentWithVBA** 文件的位置。 如果您使用已啟用巨集的自有文件，則改為指定該文件的位置。

9. 按一下 [完成] 。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在設計工具中開啟 **DocumentWithVBA** 檔，並將 **CallingCodeFromVBA** 專案新增至 **方案總管**。

## <a name="trust-the-location-of-the-document"></a>信任檔的位置
 您必須先信任文件中要執行的 VBA，才能將方案中的程式碼公開至文件中的 VBA 程式碼。 有數種方法能完成這項操作。 針對此逐步解說，是在 Word 中的 [信任中心]  信任文件的位置。

### <a name="to-trust-the-location-of-the-document"></a>信任文件的位置

1. 啟動 Word。

2. 按一下 [檔案]  索引標籤。

3. 按一下 [Word 選項]  按鈕。

4. 在分類窗格中，按一下 [信任中心] 。

5. 在詳細資料窗格中，按一下 [信任中心設定] 。

6. 在分類窗格中，按一下 [信任位置] 。

7. 在詳細資料窗格中，按一下 [新增位置] 。

8. 在 [Microsoft Office 信任位置]  對話方塊中，瀏覽至包含 [CallingCodeFromVBA]  專案的資料夾。

9. 選取 [同時信任此位置的子資料夾] 。

10. 按一下 [Microsoft Office 信任位置]  對話方塊中的 [確定] 。

11. 按一下 [信任中心]  對話方塊中的 [確定] 。

12. 按一下 [Word 選項]  對話方塊中的 [確定] 。

13. 結束 Word。

## <a name="add-a-method-to-the-thisdocument-class"></a>將方法新增至 ThisDocument 類別
 目前已設定 VBA 專案，請將方法加入您可以從 VBA 程式碼呼叫的 `ThisDocument` 主項目類別。

### <a name="to-add-a-method-to-the-thisdocument-class"></a>將方法加入 ThisDocument 類別

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ThisDocument.vb] ，然後按一下 [檢視程式碼] 。

     **ThisDocument.vb** 檔案隨即在 [程式碼編輯器] 中開啟。

2. 將下列方法新增至 `ThisDocument` 類別。 此方法會在文件開頭建立有兩列和兩欄的資料表。 此參數指定第一列中顯示的文字。 稍後在本逐步解說中，您會從本文件中的 VBA 程式碼呼叫此方法。

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. 建置專案。

## <a name="expose-the-method-to-vba-code"></a>將方法公開至 VBA 程式碼
 若要將 `CreateTable` 方法公開至文件中的 VBA 程式碼，請將 **主項目的** EnableVbaCallers `ThisDocument` 屬性設定為 [True] 。

### <a name="to-expose-the-method-to-vba-code"></a>將方法公開至 VBA 程式碼

1. 按兩下 [方案總管] 中的 **ThisDocument.vb**。

     **DocumentWithVBA** 檔案隨即在設計工具中開啟。

2. 在 [屬性]  視窗中，選取 **EnableVbaCallers** 屬性，然後將值變更為 [True] 。

3. 按一下訊息中顯示的 [確定]  。

4. 建置專案。

## <a name="call-the-method-from-vba-code"></a>從 VBA 程式碼呼叫方法
 您現在可以從文件中的 VBA 程式碼呼叫 `CreateTable` 方法。

> [!NOTE]
> 在這個逐步解說中，您會在偵錯專案時將 VBA 程式碼加入文件。 您加入此文件的 VBA 程式碼將會在下一次建置專案時被覆寫，因為 Visual Studio 會將組建輸出資料夾中的文件取代為來自主要專案資料夾的文件複本。 如果您要儲存 VBA 程式碼，可以將它複製到專案資料夾的文件中。 如需詳細資訊，請參閱 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

### <a name="to-call-the-method-from-vba-code"></a>從 VBA 程式碼呼叫方法

1. 按 **F5** 執行您的專案。

2. 在 [開發人員]  索引標籤上的 [程式碼]  群組中，按一下 [Visual Basic] 。

     [Visual Basic 編輯器] 隨即開啟。

3. 按一下 [插入]  功能表上的 [模組] 。

4. 將下列程式碼加入新模組。

     這段程式碼會呼叫自訂組件中的 `CreateTable` 方法。 該巨集會使用 `CallVSTOAssembly` 物件的 `ThisDocument` 屬性存取此方法。 當您稍早在本逐步解說中設定 **EnableVbaCallers** 屬性時，便已自動產生這個屬性。

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. 按 **F5**。

6. 驗證新資料表是否已加入文件。

7. 結束 Word 但不儲存變更。

## <a name="next-steps"></a>後續步驟
 您可以在這些主題中，進一步了解如何從 VBA 呼叫 Office 方案中的程式碼：

- 從 VBA 呼叫在 Visual C# 自訂中的程式碼。 此處理序與 Visual Basic 處理序不同。 如需詳細資訊，請參閱 [逐步解說：從 Visual C&#35; 專案中的 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。

- 從 VBA 呼叫 VSTO 增益集中的程式碼。 如需詳細資訊，請參閱 [逐步解說：從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。

## <a name="see-also"></a>另請參閱
- [合併 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
- [如何：將程式碼公開給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [如何：將程式碼公開給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [逐步解說：在 Visual C&#35; 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
