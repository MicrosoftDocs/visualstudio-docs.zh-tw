---
title: 如何： 公開程式碼給 Visual C# 專案中的 VBA |Microsoft 文件
ms.custom: ''
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7564d64763549f2fefe8e0a8b9813fdef9a16b6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>如何：公開程式碼給 Visual C# 專案中的 VBA
  如果您想要與彼此互動的程式碼的兩個類型，您可以公開的 Visual C# 專案給 Visual Basic for Applications (VBA) 程式碼中的程式碼。  
  
 Visual C# 處理序會與 Visual Basic 處理序不同。 如需詳細資訊，請參閱[如何： 公開程式碼給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Visual C# 專案中公開程式碼  
 若要啟用 Visual C# 專案中呼叫程式碼的 VBA 程式碼，修改的程式碼，所以為 COM 可見，並將**ReferenceAssemblyFromVbaProject**屬性**True**設計工具中。  
  
 如需示範如何從 VBA 呼叫 Visual C# 專案中的一種方法的逐步解說，請參閱[逐步解說： 呼叫 Visual C 中的 VBA 程式碼&#35;專案](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)。  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>若要公開給 VBA 的 Visual C# 專案中的程式碼  
  
1.  開啟或建立 Word 文件、 Excel 活頁簿或 Excel 範本支援的巨集，並已包含 VBA 程式碼為基礎的文件層級專案。  
  
     如需支援的巨集的文件的檔案格式的詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能無法用於 Word 範本專案。  
  
2.  確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3.  新增您想要公開給 VBA，若要在專案中，在公用類別成員，並宣告做為新的成員**公用**。  
  
4.  套用下列<xref:System.Runtime.InteropServices.ComVisibleAttribute>和<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性加入您要公開給 VBA 的類別。 這些屬性可以讓 COM 看到類別，但是不會產生類別介面。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  覆寫**GetAutomationObject**傳回給 VBA 之類別所公開的執行個體的專案中的主項目類別的方法：  
  
    -   如果您正在公開給 VBA 之主項目類別，覆寫**GetAutomationObject**屬於這個類別，並傳回目前的執行個體類別的方法。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   如果您正在公開給 VBA 的主項目不是類別，覆寫**GetAutomationObject**之任何主機的方法在專案中，項目，並傳回非主項目類別的執行個體。 例如，下列程式碼假設您正在公開類別的`DocumentUtilities`給 VBA。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     如需主項目的詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
6.  擷取您要公開給 VBA 之類別的介面。 在**擷取介面**對話方塊方塊中，選取您想要包含在介面宣告中的公用成員。 如需詳細資訊，請參閱[擷取介面重構](../ide/reference/extract-interface.md)。
  
7.  新增**公用**關鍵字加入介面宣告。  
  
8.  讓介面的 COM 可以看見，加入下列<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性至介面。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. 在設計師中開啟的文件 （適用於 Word) 或 （針對 Excel) 的工作表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
10. 在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任而得以執行，您會收到錯誤訊息，當您設定**ReferenceAssemblyFromVbaProject**屬性**True**. 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
11. 按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您加入 VBA 程式碼加入活頁簿，或文件執行中的專案時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失在下一次建置專案。 這是因為在組建中的文件輸出資料夾會覆寫每次建置專案。  
  
     此時，Visual Studio 將專案設定可讓組件呼叫 VBA 專案。 Visual Studio 也會加入名為的方法`GetManagedClass`的 VBA 專案。 您可以呼叫這個方法，從任何地方存取您公開給 VBA 之類別的 VBA 專案中。  
  
12. 建置專案。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說： 從 Visual C 中的 VBA 呼叫程式碼&#35;專案](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [如何：公開程式碼給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  