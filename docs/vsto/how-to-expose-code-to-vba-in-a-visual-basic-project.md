---
title: 如何：將程式碼公開給 Visual Basic 專案中的 VBA
description: 如果您想要讓兩種類型的程式碼彼此互動，請瞭解如何公開 Visual Basic 專案中的程式碼，以 Visual Basic for Applications (VBA) 程式碼。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913487"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>如何：將程式碼公開給 Visual Basic 專案中的 VBA
  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]如果您想要讓兩種類型的程式碼彼此互動，您可以公開專案中的程式碼，以 Visual Basic for Applications (VBA) 程式碼。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Visual Basic 進程與 Visual c # 進程不同。 如需詳細資訊，請參閱 how [to：將程式碼公開給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。

 主專案類別中程式碼的程式與其他類別中程式碼的程式不同：

- [公開主專案類別中的程式碼](#HostItemCode)

- [公開不在主專案類別中的程式碼](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> 公開主專案類別中的程式碼
 若要讓 VBA 程式碼在主專案類別中呼叫 Visual Basic 程式碼，請將主專案的 **EnableVbaCallers** 屬性設定為 **True**。

 如需示範如何公開主專案類別的方法，然後從 VBA 呼叫它的逐步解說，請參閱 [逐步解說：從 Visual Basic 專案中的 Vba 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。 如需主專案的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>若要將主專案中的程式碼公開給 VBA

1. 開啟或建立檔層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案，此專案是以支援宏的 Word 檔、excel 活頁簿或 excel 範本為基礎，而且已經包含 VBA 程式碼。

     如需有關支援宏之檔檔案格式的詳細資訊，請參閱 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

    > [!NOTE]
    > 這項功能無法用於 Word 範本專案。

2. 確定允許執行檔中的 VBA 程式碼，而不提示使用者啟用宏。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

3. 將您想要公開的屬性、方法或事件新增至專案中的其中一個主專案類別，並將新的成員宣告為 **Public**。 類別的名稱視應用程式而定：

    - 在 Word 專案中，預設會命名主專案類別 `ThisDocument` 。

    - 在 Excel 專案中，主專案類別 `ThisWorkbook` 預設為、、 `Sheet1` `Sheet2` 和 `Sheet3` 。

4. 將主專案的 **EnableVbaCallers** 屬性設定為 **True**。 在設計工具中開啟主專案時，就可以在 [ **屬性** ] 視窗中使用這個屬性。

     設定這個屬性之後，Visual Studio 會自動將 **ReferenceAssemblyFromVbaProject** 屬性設定為 **True**。

    > [!NOTE]
    > 如果活頁簿或檔尚未包含 VBA 程式碼，或檔中的 VBA 程式碼不受信任而無法執行，當您將 **EnableVbaCallers** 屬性設定為 **True** 時，您將會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

5. 按一下訊息中顯示的 [確定]  。 這則訊息會提醒您，如果您在執行專案時將 VBA 程式碼加入至活頁簿或檔，則在下次建立專案時，將會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 遺失 vba 程式碼。 這是因為每次您建立專案時，就會覆寫組建輸出檔案夾中的檔。

     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫元件。 Visual Studio 也會將名為的屬性加入 `CallVSTOAssembly` 至 `ThisDocument` `ThisWorkbook` `Sheet1` VBA 專案中的、、、 `Sheet2` 或 `Sheet3` 模組。 您可以使用這個屬性來存取您公開給 VBA 之類別的公用成員。

6. 建置專案。

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> 公開不在主專案類別中的程式碼
 若要讓 VBA 程式碼呼叫不在主專案類別中 Visual Basic 程式碼，請修改程式碼，讓 VBA 可以看到它。

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>將不在主專案類別中的程式碼公開給 VBA

1. 開啟或建立檔層級 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案，此專案是以支援宏的 Word 檔、excel 活頁簿或 excel 範本為基礎，而且已經包含 VBA 程式碼。

     如需有關支援宏之檔檔案格式的詳細資訊，請參閱 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

    > [!NOTE]
    > 這項功能無法用於 Word 範本專案。

2. 確定允許執行檔中的 VBA 程式碼，而不提示使用者啟用宏。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

3. 將您想要公開的成員新增至專案中的公用類別，並將新的成員宣告為 **公用**。

4. 將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性和 <xref:Microsoft.VisualBasic.ComClassAttribute> 屬性套用至您要公開給 VBA 的類別。 這些屬性讓 VBA 可以看見類別。

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. 覆寫專案中之主項目類別的 **GetAutomationObject** 方法，傳回您正在公開給 VBA 之類別的執行個體。 下列程式碼範例假設您要將名為的類別公開 `DocumentUtilities` 給 VBA。

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. 開啟 Word) 的檔 (或 Excel) 設計師的工作表 ([!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

7. 在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。

    > [!NOTE]
    > 如果活頁簿或檔尚未包含 VBA 程式碼，或檔中的 VBA 程式碼不受信任而無法執行，當您將 **ReferenceAssemblyFromVbaProject** 屬性設定為 **True** 時，您將會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

8. 按一下訊息中顯示的 [確定]  。 這則訊息會提醒您，如果您在執行專案時將 VBA 程式碼加入至活頁簿或檔，則在下次建立專案時，將會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 遺失 vba 程式碼。 這是因為每次您建立專案時，就會覆寫組建輸出檔案夾中的檔。

     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫元件。 Visual Studio 也會將名為 `GetManagedClass` 的方法加入至 VBA 專案。 您可以從 VBA 專案的任何位置呼叫這個方法，以存取您公開給 VBA 的類別。

9. 建置專案。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [合併 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [如何：將程式碼公開給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
