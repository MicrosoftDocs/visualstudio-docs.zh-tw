---
title: HOW TO：公開給 VBA 的程式碼，在 Visual Basic 專案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 43308e73d00f163b27a4dbe20dc9f0cbb656c4ba
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648635"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>HOW TO：公開給 VBA 的程式碼，在 Visual Basic 專案
  您的程式碼中的公開[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]如果您想要與彼此互動的程式碼的兩個類型，專案加入 Visual Basic for Applications (VBA) 程式碼。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic 程序與 Visual C# 程序不同。 如需詳細資訊，請參閱[＜How to：公開給 Visual C 中的 VBA 程式碼&#35;專案](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。  
  
 處理程序是不同的主項目類別中的程式碼比其他類別中的程式碼：  
  
- [公開 （expose) 中的主項目類別的程式碼](#HostItemCode)  
  
- [公開 （expose) 不是主項目類別的程式碼](#NonHostItem)  
  
  ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:從 VBA 呼叫 VSTO 程式碼嗎？](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> 公開 （expose) 中的主項目類別的程式碼  
 若要讓 VBA 呼叫 Visual Basic 程式碼中的主項目類別的程式碼，將**EnableVbaCallers**主項目的屬性 **，則為 True**。  
  
 如需示範如何公開主項目類別的方法，然後將它呼叫 vba 的逐步解說，請參閱[逐步解說：從 VBA 呼叫程式碼，在 Visual Basic 專案中](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。 如需主項目的詳細資訊，請參閱[主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>若要公開給 VBA 主機項目中的程式碼  
  
1.  開啟或建立文件層級[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]根據 Word 文件、 Excel 活頁簿或 Excel 範本支援巨集，並已包含 VBA 程式碼的專案。  
  
     如需有關支援的巨集的文件檔案格式的詳細資訊，請參閱 <<c0> [ 合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能無法用於 Word 範本專案。  
  
2.  請確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3.  新增屬性、 方法或您想要公開給 VBA 的主項目類別，在您的專案，其中一個事件，並宣告做為新的成員**公開**。 類別的名稱需視應用程式而定：  
  
    -   在 Word 專案，主項目類別的名稱為`ThisDocument`預設。  
  
    -   在 Excel 專案中，主項目類別名為`ThisWorkbook`， `Sheet1`， `Sheet2`，和`Sheet3`預設。  
  
4.  設定**EnableVbaCallers**主項目的屬性 **，則為 True**。 此屬性位於**屬性**主機項目時的設計工具中開啟的視窗。  
  
     您設定此屬性之後，Visual Studio 會自動設定**ReferenceAssemblyFromVbaProject**屬性設 **，則為 True**。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任執行，您就會收到錯誤訊息，當您設定**EnableVbaCallers**屬性設 **，則為 True**。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
5.  按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或文件，而您正在從專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失您建置專案的下一次。 這是因為每次建置專案，則會覆寫組建輸出資料夾中的文件。  
  
     此時，Visual Studio 設定專案，以便可以呼叫組件的 VBA 專案。 Visual Studio 也會加入名為的屬性`CallVSTOAssembly`要`ThisDocument`， `ThisWorkbook`， `Sheet1`， `Sheet2`，或`Sheet3`模組中的 VBA 專案。 您可以使用這個屬性來存取您公開給 VBA 之類別的公用成員。  
  
6.  建置專案。  
  
##  <a name="NonHostItem"></a> 公開 （expose) 不是主項目類別的程式碼  
 若要啟用 VBA 程式碼呼叫不是主項目類別中的 Visual Basic 程式碼，請修改程式碼，因此它會顯示給 VBA。  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>若要公開給 VBA 之主項目類別中不是程式碼  
  
1.  開啟或建立文件層級[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]根據 Word 文件、 Excel 活頁簿或 Excel 範本支援巨集，並已包含 VBA 程式碼的專案。  
  
     如需有關支援的巨集的文件檔案格式的詳細資訊，請參閱 <<c0> [ 合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能無法用於 Word 範本專案。  
  
2.  請確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3.  新增您想要在專案中的公用類別公開給 VBA 的成員，並宣告做為新的成員**公開**。  
  
4.  套用下列<xref:System.Runtime.InteropServices.ComVisibleAttribute>和<xref:Microsoft.VisualBasic.ComClassAttribute>屬性到您要公開給 VBA 的類別。 這些屬性可以讓顯示給 VBA 的類別。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  覆寫專案中之主項目類別的 **GetAutomationObject** 方法，傳回您正在公開給 VBA 之類別的執行個體。 下列程式碼範例假設您正在公開一個名為類別`DocumentUtilities`給 VBA。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  （針對 Word) 的文件或 （適用於 Excel) 的工作表設計工具中開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
7.  在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任執行，您就會收到錯誤訊息，當您設定**ReferenceAssemblyFromVbaProject**屬性設 **，則為 True**. 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
8.  按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或文件，而您正在從專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失您建置專案的下一次。 這是因為每次建置專案，則會覆寫組建輸出資料夾中的文件。  
  
     此時，Visual Studio 設定專案，以便可以呼叫組件的 VBA 專案。 Visual Studio 也會加入一個名為方法`GetManagedClass`的 VBA 專案。 您可以呼叫這個方法，從任何地方存取您公開給 VBA 之類別的 VBA 專案中。  
  
9. 建置專案。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說：在 Visual Basic 專案中，從 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [如何：公開給 Visual C 中的 VBA 程式碼&#35;專案](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  