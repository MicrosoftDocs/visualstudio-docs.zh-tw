---
title: 如何： 定義和使用工作流程設計工具中的活動委派 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f99816153870884f868a6b229068bdc281408337
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865488"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派
[!INCLUDE[net_v45](../includes/net-v45-md.md)] 包含用於 <xref:System.Activities.Statements.InvokeDelegate> 活動的全新設計工具。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。  
  
### <a name="define-an-activity-delegate"></a>定義活動委派  
  
1. 在  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]，選取**檔案**，**新增**，**專案**。 選取**工作流程**節點，在左側，而**工作流程主控台應用程式**右側的範本。 （如有需要） 的專案命名，然後按一下**Ok**。  
  
2. 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**新增**，**新項目...**. 選取**工作流程**節點，在左側，而**活動**右側的範本。 新活動命名**MyForEach.xaml**然後按一下**確定**。 活動會在工作流程設計工具中開啟。  
  
3. 在工作流程設計工具中，按一下**引數** 索引標籤。  
  
4. 按一下  **Vytvořit Argument**。 命名新的引數**項目**。  
  
5. 在 **引數型別**欄中，選取**的 [T] 陣列**。  
  
6. 在型別瀏覽器中，選取**物件**。 按一下  **Ok**。  
  
7. 按一下 **建立引數**一次。 命名新的引數**主體**。 在 **方向**資料行的新引數，選取**屬性**。  
  
8. 在 [引數類型] 欄中，選取**Vyhledat typy...**  
  
9. 在型別瀏覽器中，輸入**ActivityAction**中**型別名稱**欄位。 選取  **ActivityAction\<T >** 樹狀檢視中。 選取 **物件**似乎指派類型下拉式清單中**ActivityAction\<物件 >** 引數。  
  
10. 拖曳<xref:System.Activities.Statements.While>活動，從**控制流程**工具箱拖曳至設計工具介面的一部分。  
  
11. 選取 [<xref:System.Activities.Statements.While>活動，然後選取**變數**] 索引標籤。  
  
12. 選取 **建立的變數**。 新的變數命名**Index**。  
  
13. 在 **變數的型別**欄中，選取**Int32**。 離開**範圍**做為**雖然**，而**預設**資料行保留空白。  
  
14. 設定**條件**屬性<xref:System.Activities.Statements.While>活動**index < Items.Length;**。  
  
15. 拖曳<xref:System.Activities.Statements.InvokeDelegate>活動，從**基本型別**工具箱的區段**主體**的<xref:System.Activities.Statements.While>活動。  
  
16. 選取 **主體**委派下拉式清單中。  
  
17. 在 **屬性**方格<xref:System.Activities.Statements.InvokeDelegate>活動中，按一下  **...** 按鈕**委派的引數**屬性。  
  
18. 在 **值**具名引數的資料行**引數**，輸入**Items [Index]**。 按一下  **Ok**以關閉**DelegateArguments**對話方塊。  
  
19. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 <xref:System.Activities.Statements.Assign>將建立活動，以及<xref:System.Activities.Statements.Sequence>活動將會自動建立包含兩個活動中的**主體**一節**MyForEach**活動。 需要此序列，因為**主體**區段只能包含單一活動。 自動建立新的 <xref:System.Activities.Statements.Sequence> 活動是 [!INCLUDE[net_v45](../includes/net-v45-md.md)] 的新功能。  
  
20. 設定**要**屬性<xref:System.Activities.Statements.Assign>活動**index**。 設定**值**屬性**指派**活動**index+1**。  
  
    自訂**MyForEach**活動會立即叫用一次來傳給它透過每個值的任意活動**項目**集合，做為活動輸入集合中的值。  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動  
  
1. 建置專案，藉由按下**Ctrl + Shift + B**。  
  
2. 在 **方案總管**，開啟**Workflow1.xaml**設計工具中。  
  
3. 拖曳**MyForEach**從工具箱拖曳至設計工具介面的活動。 活動將會在工具箱的區段中，名稱與專案的名稱相同。  
  
4. 設定**項目**屬性**MyForEach**活動**new Object [] {1，"abc"}**。  
  
5. 拖曳<xref:System.Activities.Statements.WriteLine>活動，從**基本型別**工具箱的區段**Delegate: Body**一節**MyForEach**活動。  
  
6. 設定**文字**屬性<xref:System.Activities.Statements.WriteLine>活動**argument.tostring （)**。  
  
   當執行工作流程時，主控台將顯示以下資訊：  
  
   **1**   
   **abc**