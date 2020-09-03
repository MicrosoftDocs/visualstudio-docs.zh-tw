---
title: 如何：定義和使用工作流程設計工具中的活動委派 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603860"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派
[!INCLUDE[net_v45](../includes/net-v45-md.md)] 包含活動的新預設設計工具 <xref:System.Activities.Statements.InvokeDelegate> 。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

### <a name="define-an-activity-delegate"></a>定義活動委派

1. 在中 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ， **File**選取 [檔案]、[**新增**]、[**專案**]。 選取左側的 [ **工作流程** ] 節點，右邊的 [ **工作流程主控台應用程式** ] 範本。 視需要將專案命名為 () 然後按一下 **[確定]**。

2. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **加入**]、[ **新增專案 ...**]。 選取左側的 **工作流程** 節點和右邊的 **活動** 範本。 將新活動命名為 **MyForEach** ，然後按一下 **[確定]**。 活動會在工作流程設計工具中開啟。

3. 在工作流程設計工具中，按一下 [ **引數** ] 索引標籤。

4. 按一下 **[建立引數]**。 命名新的引數 **專案**。

5. 在 [ **引數類型** ] 資料行中，選取 **[T] 的陣列**。

6. 在類型瀏覽器中，選取 [  **物件**]。 按一下 [確定]  。

7. 再次按一下 [ **建立引數** ]。 將新引數命名為 **Body**。 在新引數的 [ **方向** ] 資料行中，選取 [ **屬性**]。

8. 在 [引數類型] 資料行中，選取 **[流覽類型 ...]** 。

9. 在類型瀏覽器的 [**類型名稱**] 欄位中，輸入**ActivityAction** 。 在樹狀檢視中選取 [ **ActivityAction \<T> ** ]。 在出現的下拉式清單中選取 [**物件**]，以將類型**ActivityAction \<Object> **指派給引數。

10. 將 [ <xref:System.Activities.Statements.While> 工具箱] 的 [ **控制流程** ] 區段中的活動拖曳至設計工具介面。

11. 選取 <xref:System.Activities.Statements.While> 活動，然後選取 [ **變數** ] 索引標籤。

12. 選取 [ **建立變數**]。 命名新的變數 **索引**。

13. 在 [ **變數類型** ] 資料行中，選取 [ **Int32**]。 將**範圍****保持在 [時間]，並**將 [**預設**] 資料行保留空白。

14. 將活動的 [ **條件** ] 屬性設定 <xref:System.Activities.Statements.While> 為 [ **索引 < 專案]。 [長度];**。

15. 將 <xref:System.Activities.Statements.InvokeDelegate> [工具箱] 的 [ **基本** ] 區段中的活動拖曳至活動的 **主體** <xref:System.Activities.Statements.While> 。

16. 選取 [委派] 下拉式清單中的 [ **主體** ]。

17. 在活動的 [ **屬性** ] 方格中 <xref:System.Activities.Statements.InvokeDelegate> ，按一下 **...** 按鈕（位於 [ **委派引數** ] 屬性中）。

18. 在引數命名**參數**的 [**值**] 資料行中，輸入**Items [Index]**。 按一下 **[確定** ] 以關閉 [ **DelegateArguments** ] 對話方塊。

19. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 <xref:System.Activities.Statements.Assign>將會建立活動，並且會 <xref:System.Activities.Statements.Sequence> 自動建立活動，以在**MyForEach**活動的 [**主體**] 區段中包含兩個活動。 順序是必要的，因為 **Body** 區段只能包含單一活動。 自動建立新的 <xref:System.Activities.Statements.Sequence> 活動是 [!INCLUDE[net_v45](../includes/net-v45-md.md)] 的新功能。

20. 將活動的 [ **到** ] 屬性設定 <xref:System.Activities.Statements.Assign> 為 [ **索引**]。 將 [**指派**] 活動的 [**值**] 屬性設定為 [**索引 + 1**]。

    自訂 **MyForEach** 活動現在會針對每個透過 **Items** 集合傳遞給它的值叫用任意活動一次，並將集合中的值做為活動的輸入。

### <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動

1. 按下 **Ctrl + Shift + B**以建立專案。

2. 在**方案總管**中，在設計工具中開啟**workflow1.xaml。**

3. 將 [ **MyForEach** ] 活動從 [工具箱] 拖曳至設計工具介面。 活動將會在工具箱的區段中，名稱與專案的名稱相同。

4. 將**MyForEach**活動的**Items**屬性設為**new Object [] {1，"abc"}**。

5. 將 [ <xref:System.Activities.Statements.WriteLine> 工具箱] 的 [**基本**] 區段中的活動拖曳至**MyForEach**活動的 [**委派： Body** ] 區段。

6. 將活動的**Text**屬性設定 <xref:System.Activities.Statements.WriteLine> 為** ( # B1 的引數。**

   當執行工作流程時，主控台將顯示以下資訊：

   **1** 
   **abc**