---
title: 工作流程設計工具：定義和使用活動委派
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 41271266793927f6029f50c0411bb9a150f5a64a
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817498"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派

.NET Framework 4.5 包含適用于活動的現成設計工具 <xref:System.Activities.Statements.InvokeDelegate> 。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

## <a name="define-an-activity-delegate"></a>定義活動委派

1. 建立新的**工作流程主控台應用程式**專案。

   > [!NOTE]
   > 如果您看不到**工作流程**專案範本，請先安裝 Visual Studio 的**Windows Workflow Foundation**元件。 如需詳細指示，請參閱[Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

3. 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入**  >  **新專案**]。 選取 [**工作流程**] 分類，然後選取 [**活動**專案] 範本。 將新活動命名為**MyForEach** ，然後選取 **[確定]**。

   活動會在工作流程設計工具中開啟。

4. 在 [工作流程設計工具中，按一下 [**引數**] 索引標籤。

5. 按一下 **[建立引數]**。 將新引數命名為**Items**。

6. 在 [**引數類型**] 資料行中，選取 **[T] 的陣列**。

7. 在 [類型瀏覽器] 中，選取 [**物件**]，然後選取 **[確定]**。

8. 再次按一下 [**建立引數**]。 將新的引數命名為**主體**。 在新引數的 [**方向**] 資料行中，選取 [**屬性**]。

9. 在 [引數類型] 資料行中，選取 **[流覽類型]**

10. 在類型瀏覽器的 [**類型名稱**] 欄位中，輸入**ActivityAction** 。 在樹狀檢視中選取 [ **ActivityAction \<T> ** ]。 在出現的下拉式清單中選取 [**物件**]，將類型**ActivityAction \<Object> **指派給引數。

11. 從 [ <xref:System.Activities.Statements.While> 工具箱] 的 [**控制流程**] 區段，將活動拖曳至設計工具介面。

12. 選取 <xref:System.Activities.Statements.While> 活動，然後選取 [**變數**] 索引標籤。

13. 選取 [**建立變數**]。 將新變數命名為**Index**。

14. 在 [**變數類型**] 資料行中，選取 [ **Int32**]。 將**範圍**保持為 [ **While**]，並將 [**預設**] 資料行保留空白。

15. 將活動的 [**條件**] 屬性設定 <xref:System.Activities.Statements.While> 為 [索引] **< 專案. [長度];**。

16. 將 [ <xref:System.Activities.Statements.InvokeDelegate> 工具箱] 的 [**基本**] 區段中的活動拖曳至活動的 [**主體**] <xref:System.Activities.Statements.While> 。

17. 選取 [委派] 下拉式集中的 [**主體**]。

18. 在活動的 [**屬性**] 方格中 <xref:System.Activities.Statements.InvokeDelegate> ，按一下 [**委派引數**] 屬性中的 [ **...** ] 按鈕。

19. 在名為**argument**之引數的 [**值**] 資料行中，輸入**Items [Index]**。 按一下 **[確定**] 關閉 [ **DelegateArguments** ] 對話方塊。

20. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 <xref:System.Activities.Statements.Assign>隨即會建立活動，並 <xref:System.Activities.Statements.Sequence> 自動建立活動，以包含**MyForEach**活動的 [內文**Body** ] 區段中的兩個活動。 順序是必要的，因為**Body**區段只能包含單一活動。 自動建立新 <xref:System.Activities.Statements.Sequence> 活動是 .NET Framework 4.5 的新功能。

21. 將活動的 [ **to** ] 屬性設定 <xref:System.Activities.Statements.Assign> 為 [ **index**]。 將 [**指派**] 活動的 [**值**] 屬性設定為 [**索引 + 1**]。

    自訂**MyForEach**活動會針對每個透過**Items**集合傳入的值叫用一次任意活動，並以集合中的值做為活動的輸入。

## <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動

1. 按**Ctrl** + **Shift** + **B**來建立專案。

2. 在**方案總管**中，在設計工具中開啟**workflow1.xaml。**

3. 將 [ **MyForEach** ] 活動從 [工具箱] 拖曳至設計工具介面。 活動位於工具箱的區段中，其名稱與專案相同。

4. 將**MyForEach**活動的**Items**屬性設定為**new Object [] {1，"abc"}**。

5. 將 [ <xref:System.Activities.Statements.WriteLine> 工具箱] 的 [**基本**] 區段中的活動拖曳至 [ **MyForEach** ] 活動的 [**委派：主體**] 區段。

6. 將活動的**Text**屬性設定 <xref:System.Activities.Statements.WriteLine> 為**引數 ToString （）**。

執行工作流程時，主控台會顯示下列輸出：

**1** 
**abc**
