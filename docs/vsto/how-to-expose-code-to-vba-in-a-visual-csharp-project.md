---
title: HOW TO：公開給 VBA 中的程式碼C#專案
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f0b3f004f6aebed6426238a081369c7d50e15f5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648505"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>HOW TO：公開 （expose) 至視覺效果中的 VBA 程式碼C#專案
  如果您想要與彼此互動的程式碼的兩個類型，您可以公開 Visual C# 專案中 Visual basic for Applications (VBA) 程式碼的程式碼。  
  
 Visual C# 程序與 Visual Basic 處理序不同。 如需詳細資訊，請參閱[＜How to：公開給 VBA 的程式碼，在 Visual Basic 專案中](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Visual C# 專案中的程式碼公開 （expose)  
 若要讓 VBA 呼叫 Visual C# 專案中的程式碼的程式碼，修改的程式碼，因此它是為 COM 可見，並將**ReferenceAssemblyFromVbaProject**屬性設 **，則為 True**設計工具中。  
  
 如需示範如何在視覺效果中呼叫方法的逐步解說C#從 VBA 專案，請參閱[逐步解說：從 Visual C 中的 VBA 呼叫程式碼&#35;專案](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>若要公開給 VBA 的 Visual C# 專案中的程式碼  
  
1. 開啟或建立 Word 文件、 Excel 活頁簿或 Excel 範本支援巨集，並已包含 VBA 程式碼為基礎的文件層級專案。  
  
    如需有關支援的巨集的文件檔案格式的詳細資訊，請參閱 <<c0> [ 合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
   > [!NOTE]  
   >  這項功能無法用於 Word 範本專案。  
  
2. 請確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3. 新增您想要在專案中的公用類別公開給 VBA 的成員，並宣告做為新的成員**公開**。  
  
4. 套用下列<xref:System.Runtime.InteropServices.ComVisibleAttribute>和<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性到您要公開給 VBA 的類別。 這些屬性可以讓 COM 看到類別，但是不會產生類別介面。  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. 覆寫**GetAutomationObject** ，公開類別的執行個體傳回給 VBA 專案中的主項目類別的方法：  
  
   - 如果您正在公開給 VBA 之主項目類別，覆寫**GetAutomationObject**屬於這個類別，並傳回目前的執行個體類別的方法。  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - 如果您正在公開給 VBA 的主項目不是類別，覆寫**GetAutomationObject**方法之任何主機在專案中，項目，然後傳回非主項目類別的執行個體。 例如，下列程式碼假設您正在公開一個名為類別`DocumentUtilities`給 VBA。  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     如需主項目的詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
6. 從您要公開給 VBA 的類別來擷取介面。 在 **擷取介面**對話方塊方塊中，選取您想要在介面宣告中包含的公用成員。 如需詳細資訊，請參閱 <<c0> [ 擷取介面重構](../ide/reference/extract-interface.md)。
  
7. 新增**公開**關鍵字加入介面宣告。  
  
8. 新增下列內容，讓介面為 COM 可見<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性的介面。  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. 在設計師中開啟 （針對 Word) 的文件或工作表 （針對 Excel) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
10. 在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任執行，您就會收到錯誤訊息，當您設定**ReferenceAssemblyFromVbaProject**屬性設 **，則為True**. 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
11. 按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您加入 VBA 程式碼的活頁簿，或文件時執行的專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失您建置專案的下一次。 這是因為在組建中的文件輸出資料夾中會覆寫的每次建置專案。  
  
     此時，Visual Studio 設定專案，以便可以呼叫組件的 VBA 專案。 Visual Studio 也會加入一個名為方法`GetManagedClass`的 VBA 專案。 您可以呼叫這個方法，從任何地方存取您公開給 VBA 之類別的 VBA 專案中。  
  
12. 建置專案。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說：從 Visual C 中的 VBA 呼叫程式碼&#35;專案](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [如何：公開給 VBA 的程式碼，在 Visual Basic 專案](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  