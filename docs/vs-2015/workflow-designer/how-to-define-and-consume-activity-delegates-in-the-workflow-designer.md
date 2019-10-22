---
title: 如何：在工作流程設計工具中定義和使用活動委派 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603860"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派
[!INCLUDE[net_v45](../includes/net-v45-md.md)] 包含用於 <xref:System.Activities.Statements.InvokeDelegate> 活動的全新設計工具。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

### <a name="define-an-activity-delegate"></a>定義活動委派

1. 在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 中，**選取 [** 檔案]、[**新增**]、[**專案**]。 選取左側的 [**工作流程**] 節點，以及右側的 [**工作流程主控台應用程式**] 範本。 將專案命名為（如有需要），然後按一下 **[確定]** 。

2. 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入**]、[**新增專案**]。 選取左側的 [**工作流程**] 節點，以及右側的 [**活動**] 範本。 將新活動命名為**MyForEach** ，然後按一下 **[確定]** 。 活動會在工作流程設計工具中開啟。

3. 在工作流程設計工具中，按一下 [**引數**] 索引標籤。

4. 按一下 [**建立引數**]。 將新引數命名為**Items**。

5. 在 [**引數類型**] 資料行中，選取 **[T] 的陣列**。

6. 在 [類型瀏覽器] 中，選取 [**物件**]。 按一下 **[確定]** 。

7. 再次按一下 [**建立引數**]。 將新的引數命名為**主體**。 在新引數的 [**方向**] 資料行中，選取 [**屬性**]。

8. 在 [引數類型] 資料行中，選取 **[流覽類型]** 。

9. 在類型瀏覽器的 [**類型名稱**] 欄位中，輸入**ActivityAction** 。 在樹狀檢視中選取 [ **ActivityAction \<T >** ]。 在出現的下拉式清單中選取 **物件**，將  **ActivityAction \<Object >** 的類型指派給引數。

10. 從 [工具箱] 的 [**控制流程**] 區段，將 [<xref:System.Activities.Statements.While>] 活動拖曳至設計工具介面。

11. 選取 [<xref:System.Activities.Statements.While>] 活動，然後選取 [**變數**] 索引標籤。

12. 選取 [**建立變數**]。 將新變數命名為**Index**。

13. 在 [**變數類型**] 資料行中，選取 [ **Int32**]。 將**範圍**保持為 [ **While**]，並將 [**預設**] 資料行保留空白。

14. 將 [<xref:System.Activities.Statements.While>] 活動的 [ **Condition** ] 屬性設定為 [ **< 專案的索引]。 [長度];** 。

15. 從 [工具箱] 的 [**基本**] 區段，將 [<xref:System.Activities.Statements.InvokeDelegate>] 活動拖曳至 [<xref:System.Activities.Statements.While>] 活動的 [**主體**]。

16. 選取 [委派] 下拉式集中的 [**主體**]。

17. 在 [<xref:System.Activities.Statements.InvokeDelegate>] 活動的 [**屬性**] 方格中，按一下 [ **...** ] [**委派引數**] 屬性中的按鈕。

18. 在名為**argument**之引數的 [**值**] 資料行中，輸入**Items [Index]** 。 按一下 **[確定**] 關閉 [ **DelegateArguments** ] 對話方塊。

19. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 將會建立 <xref:System.Activities.Statements.Assign> 活動，而且會自動建立 <xref:System.Activities.Statements.Sequence> 活動，以在**MyForEach**活動的 [**主體**] 區段中包含兩個活動。 順序是必要的，因為**Body**區段只能包含單一活動。 自動建立新的 <xref:System.Activities.Statements.Sequence> 活動是 [!INCLUDE[net_v45](../includes/net-v45-md.md)] 的新功能。

20. 將 <xref:System.Activities.Statements.Assign> 活動的**to**屬性設定為**index**。 將 [**指派**] 活動的 [**值**] 屬性設定為 [**索引 + 1**]。

    自訂**MyForEach**活動現在會針對每個透過**Items**集合傳入的值叫用一次任意活動，集合中的值會當做活動的輸入。

### <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動

1. 按**Ctrl + Shift + B**來建立專案。

2. 在**方案總管**中，在設計工具中開啟**workflow1.xaml。**

3. 將 [ **MyForEach** ] 活動從 [工具箱] 拖曳至設計工具介面。 活動將會在工具箱的區段中，名稱與專案的名稱相同。

4. 將**MyForEach**活動的**Items**屬性設定為**new Object [] {1，"abc"}** 。

5. 從 [工具箱] 的 [**基本**] 區段，將 [<xref:System.Activities.Statements.WriteLine>] 活動拖曳至 [ **MyForEach** ] 活動的 [**委派：主體**] 區段。

6. 將 <xref:System.Activities.Statements.WriteLine> 活動的**Text**屬性設定為**引數 ToString （）** 。

   當執行工作流程時，主控台將顯示以下資訊：

   **1** 
   **abc**