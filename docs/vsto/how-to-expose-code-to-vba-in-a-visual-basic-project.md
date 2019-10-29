---
title: 如何：將程式碼公開給 Visual Basic 專案中的 VBA
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5a0f962d93713137b23e20e35dc75108925859d
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985932"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>如何：將程式碼公開給 Visual Basic 專案中的 VBA
  如果您想要讓兩種類型的程式碼彼此互動，您可以將 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案中的程式碼公開至 Visual Basic for Applications （VBA）程式碼。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Visual Basic 程式與視覺化C#進程不同。 如需詳細資訊，請參閱[如何：在 Visual C&#35;專案中將程式碼公開給 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。

 主專案類別中的程式碼程式與其他類別中的程式碼不同：

- [公開主專案類別中的程式碼](#HostItemCode)

- [公開不在主專案類別中的程式碼](#NonHostItem)

## <a name="HostItemCode"></a>公開主專案類別中的程式碼
 若要讓 VBA 程式碼呼叫主專案類別中 Visual Basic 程式碼，請將主專案的**EnableVbaCallers**屬性設定為**True**。

 如需示範如何公開主專案類別的方法，然後從 VBA 呼叫它的逐步解說，請參閱[逐步解說：從 Visual Basic 專案中的 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。 如需主專案的詳細資訊，請參閱[主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>若要將主專案中的程式碼公開給 VBA

1. 開啟或建立以 Word 檔、Excel 活頁簿或支援宏的 Excel 範本為基礎的檔層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案，而且已經包含 VBA 程式碼。

     如需支援宏之檔檔格式的詳細資訊，請參閱[結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

    > [!NOTE]
    > 這項功能無法用於 Word 範本專案。

2. 確定允許執行檔中的 VBA 程式碼，而不提示使用者啟用宏。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

3. 將您想要公開給 VBA 的屬性、方法或事件加入至專案中的其中一個主專案類別，並將新的成員宣告為**公用**。 類別的名稱取決於應用程式：

    - 在 Word 專案中，主專案類別預設會命名為 `ThisDocument`。

    - 在 Excel 專案中，主專案類別的名稱預設為 `ThisWorkbook`、`Sheet1`、`Sheet2`和 `Sheet3`。

4. 將主專案的**EnableVbaCallers**屬性設定為**True**。 在設計工具中開啟主專案時，可以在 [**屬性**] 視窗中使用這個屬性。

     設定這個屬性之後，Visual Studio 會自動將**ReferenceAssemblyFromVbaProject**屬性設定為**True**。

    > [!NOTE]
    > 如果活頁簿或檔尚未包含 VBA 程式碼，或檔中的 VBA 程式碼不受信任而無法執行，當您將**EnableVbaCallers**屬性設定為**True**時，將會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

5. 按一下訊息中顯示的 [確定] 。 當您從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]執行專案時，此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或檔，則下一次建立專案時，VBA 程式碼將會遺失。 這是因為每次建立專案時，都會覆寫組建輸出檔案夾中的檔。

     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫元件。 Visual Studio 也會將名為 `CallVSTOAssembly` 的屬性加入至 VBA 專案中的 `ThisDocument`、`ThisWorkbook`、`Sheet1`、`Sheet2`或 `Sheet3` 模組。 您可以使用這個屬性來存取您公開給 VBA 之類別的公用成員。

6. 建置專案。

## <a name="NonHostItem"></a>公開不在主專案類別中的程式碼
 若要讓 VBA 程式碼呼叫不在主專案類別中 Visual Basic 程式碼，請修改該程式碼，讓 VBA 能夠看到它。

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>將不在主專案類別中的程式碼公開至 VBA

1. 開啟或建立以 Word 檔、Excel 活頁簿或支援宏的 Excel 範本為基礎的檔層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案，而且已經包含 VBA 程式碼。

     如需支援宏之檔檔格式的詳細資訊，請參閱[結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

    > [!NOTE]
    > 這項功能無法用於 Word 範本專案。

2. 確定允許執行檔中的 VBA 程式碼，而不提示使用者啟用宏。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

3. 將您想要公開給 VBA 的成員加入至專案中的公用類別，並將新的成員宣告為**公用**。

4. 將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 <xref:Microsoft.VisualBasic.ComClassAttribute> 屬性套用至您要公開給 VBA 的類別。 這些屬性會讓 VBA 能夠看到此類別。

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. 覆寫專案中之主項目類別的 **GetAutomationObject** 方法，傳回您正在公開給 VBA 之類別的執行個體。 下列程式碼範例假設您要將名為 `DocumentUtilities` 的類別公開至 VBA。

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中開啟檔（適用于 Word）或工作表（適用于 Excel）設計工具。

7. 在 [屬性] 視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True]。

    > [!NOTE]
    > 如果活頁簿或檔尚未包含 VBA 程式碼，或檔中的 VBA 程式碼不受信任而無法執行，當您將**ReferenceAssemblyFromVbaProject**屬性設定為**True**時，將會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

8. 按一下訊息中顯示的 [確定] 。 當您從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]執行專案時，此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或檔，則下一次建立專案時，VBA 程式碼將會遺失。 這是因為每次建立專案時，都會覆寫組建輸出檔案夾中的檔。

     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫元件。 Visual Studio 也會將名為 `GetManagedClass` 的方法加入至 VBA 專案。 您可以從 VBA 專案中的任何位置呼叫此方法，以存取您公開給 VBA 的類別。

9. 建置專案。

## <a name="see-also"></a>請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [逐步解說：從 Visual Basic 專案中的 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [如何：在 Visual C&#35;專案中將程式碼公開給 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
