---
title: 工作流程設計工具-如何：定義並取用活動委派
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c455f36d17b761fe02b7d78e96fbf2c4582d490d
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415807"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派

.NET framework 4.5 還包括全新的設計工具<xref:System.Activities.Statements.InvokeDelegate>活動。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

## <a name="define-an-activity-delegate"></a>定義活動委派

1. 建立新**工作流程主控台應用程式**專案。

   > [!NOTE]
   > 如果您沒有看到**工作流程**專案範本，請先安裝**Windows Workflow Foundation** Visual Studio 的元件。 如需詳細指示，請參閱 <<c0> [ 安裝的 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

3. 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。 選取 **工作流程**類別目錄，然後選取**活動**項目範本。 新活動命名**MyForEach.xaml** ，然後選取**確定**。

   活動會在 工作流程設計工具中開啟。

4. 在工作流程設計工具中，按一下**引數** 索引標籤。

5. 按一下  **Vytvořit Argument**。 命名新的引數**項目**。

6. 在 **引數型別**欄中，選取**的 [T] 陣列**。

7. 在型別瀏覽器中，選取**物件**，然後選取**確定**。

8. 按一下 **建立引數**一次。 命名新的引數**主體**。 在 **方向**資料行的新引數，選取**屬性**。

9. 在 [引數類型] 欄中，選取**瀏覽型別**

10. 在型別瀏覽器中，輸入**ActivityAction**中**型別名稱**欄位。 選取  **ActivityAction\<T >** 樹狀檢視中。 選取 **物件**似乎指派類型下拉式清單中**ActivityAction\<物件 >** 引數。

11. 拖曳<xref:System.Activities.Statements.While>活動，從**控制流程**工具箱拖曳至設計工具介面的一部分。

12. 選取 [<xref:System.Activities.Statements.While>活動，然後選取**變數**] 索引標籤。

13. 選取 **建立的變數**。 新的變數命名**Index**。

14. 在 **變數的型別**欄中，選取**Int32**。 離開**範圍**做為**雖然**，而**預設**資料行保留空白。

15. 設定**條件**屬性<xref:System.Activities.Statements.While>活動**index < Items.Length;**。

16. 拖曳<xref:System.Activities.Statements.InvokeDelegate>活動，從**基本型別**工具箱的區段**主體**的<xref:System.Activities.Statements.While>活動。

17. 選取 **主體**委派下拉式清單中。

18. 在 **屬性**方格<xref:System.Activities.Statements.InvokeDelegate>活動中，按一下  **...** 按鈕**委派引數**屬性。

19. 在 **值**具名引數的資料行**引數**，輸入**Items [Index]**。 按一下  **Ok**以關閉**DelegateArguments**對話方塊。

20. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 <xref:System.Activities.Statements.Assign>建立活動時，以及<xref:System.Activities.Statements.Sequence>活動會自動建立包含兩個活動中的**主體**一節**MyForEach**活動。 需要此序列，因為**主體**區段只能包含單一活動。 自動建立新<xref:System.Activities.Statements.Sequence>活動是.NET Framework 4.5 的新功能。

21. 設定**要**屬性<xref:System.Activities.Statements.Assign>活動**index**。 設定**值**屬性**指派**活動**index+1**。

    自訂**MyForEach**活動會叫用一次來傳給它透過每個值的任意活動**項目**集合，做為活動輸入集合中的值。

## <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動

1.  建置專案，藉由按下**Ctrl**+**Shift**+**B**。

2.  在 **方案總管**，開啟**Workflow1.xaml**設計工具中。

3.  拖曳**MyForEach**從工具箱拖曳至設計工具介面的活動。 活動是在與專案同名的工具箱 的區段中。

4.  設定**項目**屬性**MyForEach**活動**new Object [] {1，"abc"}**。

5.  拖曳<xref:System.Activities.Statements.WriteLine>活動，從**基本型別**工具箱的區段**Delegate: Body**一節**MyForEach**活動。

6.  設定**文字**屬性<xref:System.Activities.Statements.WriteLine>活動**argument.tostring （)**。

工作流程執行時，主控台會顯示下列輸出：

**1**
**abc**