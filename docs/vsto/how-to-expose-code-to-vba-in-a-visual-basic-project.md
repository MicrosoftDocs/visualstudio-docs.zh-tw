---
title: "如何： 公開程式碼給 Visual Basic 專案中的 VBA |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 90f97a36b3293ad2e8f3c6ab046b500ab30d4c83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>How to: Expose Code to VBA in a Visual Basic Project
  您的程式碼中的公開[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]如果您想要與彼此互動的程式碼的兩個類型，專案加入 Visual Basic for Applications (VBA) 程式碼。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic 處理序會與 Visual C# 處理序不同。 如需詳細資訊，請參閱[如何： 公開程式碼給 Visual C# 35; 中的 VBA專案](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。  
  
 比其他類別中的程式碼用於不同的主項目類別中的程式碼為處理程序：  
  
-   [公開主項目類別中的程式碼](#HostItemCode)  
  
-   [公開不是主項目類別中的程式碼](#NonHostItem)  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 呼叫 VSTO 程式碼從 VBA？](http://go.microsoft.com/fwlink/?LinkId=136757)。  
  
##  <a name="HostItemCode"></a>公開主項目類別中的程式碼  
 若要啟用 Visual Basic 程式碼呼叫的主項目類別中的 VBA 程式碼，將**EnableVbaCallers**屬性主項目的**True**。  
  
 如需示範如何公開主項目類別的方法，然後將它從 VBA 呼叫的逐步解說，請參閱[逐步解說： 從 VBA 在 Visual Basic 專案中呼叫的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)。 如需主項目的詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>若要公開給 VBA 之主項目的程式碼  
  
1.  開啟或建立文件層級[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]Word 文件、 Excel 活頁簿或 Excel 範本支援的巨集，並已包含 VBA 程式碼為基礎的專案。  
  
     如需支援的巨集的文件的檔案格式的詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能無法用於 Word 範本專案。  
  
2.  確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3.  加入屬性、 方法或您想要公開給 VBA，在專案中，主項目類別的其中一個事件，並做為新的成員宣告**公用**。 類別的名稱取決於應用程式：  
  
    -   在 Word 專案，主項目類別名稱為`ThisDocument`預設。  
  
    -   在 Excel 專案中，主項目類別名為`ThisWorkbook`， `Sheet1`， `Sheet2`，和`Sheet3`預設。  
  
4.  設定**EnableVbaCallers**屬性主項目的**True**。 這個屬性是用於**屬性**主項目的設計工具中開啟時，視窗。  
  
     將此屬性設定之後，Visual Studio 會自動設定**ReferenceAssemblyFromVbaProject**屬性**True**。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任而得以執行，您會收到錯誤訊息，當您設定**EnableVbaCallers**屬性**True**。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
5.  按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或文件，而您正在從專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失您下次建置專案。 這是因為每次建置專案，就會覆寫將組建輸出資料夾中的文件。  
  
     此時，Visual Studio 將專案設定可讓組件呼叫 VBA 專案。 Visual Studio 也會加入名為的屬性`CallVSTOAssembly`至`ThisDocument`， `ThisWorkbook`， `Sheet1`， `Sheet2`，或`Sheet3`模組中的 VBA 專案。 您可以使用這個屬性來存取您公開給 VBA 之類別的公用成員。  
  
6.  建置專案。  
  
##  <a name="NonHostItem"></a>公開不是主項目類別中的程式碼  
 若要啟用 VBA 程式碼呼叫不是主項目類別中的 Visual Basic 程式碼，請修改程式碼，因此它會顯示給 VBA。  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>若要公開給 VBA 之主項目類別不是程式碼  
  
1.  開啟或建立文件層級[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]Word 文件、 Excel 活頁簿或 Excel 範本支援的巨集，並已包含 VBA 程式碼為基礎的專案。  
  
     如需支援的巨集的文件的檔案格式的詳細資訊，請參閱[合併 VBA 和文件層級自訂](../vsto/combining-vba-and-document-level-customizations.md)。  
  
    > [!NOTE]  
    >  這項功能無法用於 Word 範本專案。  
  
2.  確定允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。  
  
3.  新增您想要公開給 VBA，若要在專案中，在公用類別成員，並宣告做為新的成員**公用**。  
  
4.  套用下列<xref:System.Runtime.InteropServices.ComVisibleAttribute>和<xref:Microsoft.VisualBasic.ComClassAttribute>屬性加入您要公開給 VBA 的類別。 這些屬性可以讓顯示給 VBA 之類別。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  覆寫專案中之主項目類別的 **GetAutomationObject** 方法，傳回您正在公開給 VBA 之類別的執行個體。 下列程式碼範例假設您正在公開類別，名為`DocumentUtilities`給 VBA。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  （適用於 Word) 的文件或 （針對 Excel) 的工作表設計工具中開啟[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
7.  在 [屬性]  視窗中，選取 **ReferenceAssemblyFromVbaProject** 屬性，然後將值變更為 [True] 。  
  
    > [!NOTE]  
    >  如果活頁簿或文件尚未包含 VBA 程式碼，或如果文件中的 VBA 程式碼不受信任而得以執行，您會收到錯誤訊息，當您設定**ReferenceAssemblyFromVbaProject**屬性**，則為 True**. 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。  
  
8.  按一下訊息中顯示的 [確定]  。 此訊息會提醒您，如果您將 VBA 程式碼加入至活頁簿或文件，而您正在從專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，VBA 程式碼將會遺失您下次建置專案。 這是因為每次建置專案，就會覆寫將組建輸出資料夾中的文件。  
  
     此時，Visual Studio 將專案設定可讓組件呼叫 VBA 專案。 Visual Studio 也會加入名為的方法`GetManagedClass`的 VBA 專案。 您可以呼叫這個方法，從任何地方存取您公開給 VBA 之類別的 VBA 專案中。  
  
9. 建置專案。  
  
## <a name="see-also"></a>請參閱  
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [逐步解說： 從 Visual Basic 專案中的 VBA 呼叫程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [如何： 公開程式碼給 Visual C# 35; 中的 VBA專案](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  