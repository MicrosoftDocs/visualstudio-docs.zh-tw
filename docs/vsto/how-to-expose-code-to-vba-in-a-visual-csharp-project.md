---
title: '如何：將程式碼公開給 c # 專案中的 VBA'
description: '如果您想要讓兩種類型的程式碼彼此互動，您可以瞭解如何在 Visual c # 專案中公開程式碼，以 Visual Basic for Applications (VBA) 程式碼。'
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1df1eed4edec3efdbf93f4effc352b3d02656d04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889404"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>如何：將程式碼公開給 Visual c # 專案中的 VBA
  如果您想要讓兩種類型的程式碼彼此互動，您可以公開 Visual c # 專案中的程式碼，以 Visual Basic for Applications (VBA) 程式碼。

 Visual c # 進程與 Visual Basic 進程不同。 如需詳細資訊，請參閱 [如何：將程式碼公開給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>公開 Visual c # 專案中的程式碼
 若要讓 VBA 程式碼呼叫 Visual c # 專案中的程式碼，請修改程式碼，讓 COM 可以看見該程式碼，然後在設計工具中將 [ **ReferenceAssemblyFromVbaProject** ] 屬性設定為 [ **True** ]。

 如需示範如何從 VBA 呼叫 Visual c # 專案中方法的逐步解說，請參閱 [逐步解說：從 Visual c&#35; 專案中的 Vba 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>將 Visual c # 專案中的程式碼公開至 VBA

1. 開啟或建立檔層級專案，此專案是以支援宏的 Word 檔、Excel 活頁簿或 Excel 範本為基礎，而且已經包含 VBA 程式碼。

    如需有關支援宏之檔檔案格式的詳細資訊，請參閱 [結合 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。

   > [!NOTE]
   > 這項功能無法用於 Word 範本專案。

2. 確定允許執行檔中的 VBA 程式碼，而不提示使用者啟用宏。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

3. 將您想要公開的成員新增至專案中的公用類別，並將新的成員宣告為 **公用**。

4. 將下列 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性和 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性套用至您要公開給 VBA 的類別。 這些屬性可以讓 COM 看到類別，但是不會產生類別介面。

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. 覆寫專案中主專案類別的 **>getautomationobject** 方法，以傳回您要公開給 VBA 之類別的實例：

   - 如果您要將主專案類別公開給 VBA，請覆寫屬於這個類別的 **>getautomationobject** 方法，並傳回類別目前的實例。

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - 如果您要將不是主專案的類別公開給 VBA，請覆寫專案中任何主專案的 **>getautomationobject** 方法，並傳回非主專案類別的實例。 例如，下列程式碼假設您要將名為的類別公開 `DocumentUtilities` 給 VBA。

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     如需主專案的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

6. 從您公開給 VBA 的類別中將介面解壓縮。 在 [ **解壓縮介面** ] 對話方塊中，選取您要包含在介面宣告中的公用成員。 如需詳細資訊，請參閱「 [解壓縮介面重構](../ide/reference/extract-interface.md)」。

7. 將 **public** 關鍵字加入至介面宣告。

8. 藉由將下列屬性新增至介面，讓 COM 看得到介面 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 。

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. 在的設計工具中開啟 Word) 的檔 (或 Excel) 的工作表 ([!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

10. 在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。

    > [!NOTE]
    > 如果活頁簿或檔尚未包含 VBA 程式碼，或檔中的 VBA 程式碼不受信任而無法執行，當您將 **ReferenceAssemblyFromVbaProject** 屬性設定為 **True** 時，您將會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

11. 按一下訊息中顯示的 [確定]  。 這則訊息會提醒您，如果您在從執行專案時將 VBA 程式碼加入至活頁簿或檔 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，vba 程式碼將會在您下一次建立專案時遺失。 這是因為每次您建立專案時，就會覆寫組建輸出檔案夾中的檔。

     此時，Visual Studio 會設定專案，讓 VBA 專案可以呼叫元件。 Visual Studio 也會將名為 `GetManagedClass` 的方法加入至 VBA 專案。 您可以從 VBA 專案的任何位置呼叫這個方法，以存取您公開給 VBA 的類別。

12. 建置專案。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [合併 VBA 和檔層級自訂](../vsto/combining-vba-and-document-level-customizations.md)
- [逐步解說：在 Visual C&#35; 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [如何：將程式碼公開給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
