---
title: "如何： 定義和使用工作流程設計工具中的活動委派 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 106ef4e7ca41fc181cc305f99e5abfce2abd825e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 包含用於 <xref:System.Activities.Statements.InvokeDelegate> 活動的全新設計工具。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。  
  
### <a name="define-an-activity-delegate"></a>定義活動委派  
  
1.  在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，選取**檔案**，**新增**，**專案**。 選取**工作流程**節點的左側，而**工作流程主控台應用程式**右邊的範本。 將專案 （如有需要），然後按一下 **確定**。  
  
2.  中的專案上按一下滑鼠右鍵**方案總管 中**選取**新增**，**新項目...**.選取**工作流程**節點的左側，而**活動**右邊的範本。 新活動**MyForEach.xaml**按一下**確定**。 活動會在工作流程設計工具中開啟。  
  
3.  在工作流程設計工具中，按一下**引數** 索引標籤。  
  
4.  按一下**建立引數**。 新引數命名**項目**。  
  
5.  在**引數型別**欄中，選取**[T] 陣列**。  
  
6.  在型別瀏覽器中，選取**物件**。 Click **Ok**.  
  
7.  按一下**建立引數**一次。 新引數命名**主體**。 在**方向**新引數，選取資料行**屬性**。  
  
8.  在引數類型 欄位中，選取**瀏覽型別...**  
  
9. 在型別瀏覽器中，輸入**ActivityAction**中**型別名稱**欄位。 選取**ActivityAction\<T >**樹狀檢視中。 選取**物件**似乎指派類型的下拉式清單中**ActivityAction\<物件 >**引數。  
  
10. 拖曳<xref:System.Activities.Statements.While>活動從**控制流程**工具箱拖曳至設計工具介面的區段。  
  
11. 選取<xref:System.Activities.Statements.While>活動，然後選取**變數** 索引標籤。  
  
12. 選取**建立變數**。 將新變數命名**索引**。  
  
13. 在**變數型別**欄中，選取**Int32**。 保留**範圍**為**時**，而**預設**空白的資料行。  
  
14. 設定**條件**屬性<xref:System.Activities.Statements.While>活動**索引 < Items.Length;**。  
  
15. 拖曳<xref:System.Activities.Statements.InvokeDelegate>活動從**基本型別**工具箱的區段**主體**的<xref:System.Activities.Statements.While>活動。  
  
16. 選取**主體**委派下拉式清單中。  
  
17. 在**屬性**方格<xref:System.Activities.Statements.InvokeDelegate>活動中，按一下  **...**按鈕**委派引數**屬性。  
  
18. 在**值**具名引數的資料行**引數**，輸入**Items [Index]**。 按一下**確定**關閉**DelegateArguments**對話方塊。  
  
19. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 <xref:System.Activities.Statements.Assign>將建立活動，以及<xref:System.Activities.Statements.Sequence>活動將會自動建立包含兩個活動中的**主體**區段**MyForEach**活動。 需要此序列，因為**主體**區段只能包含單一活動。 自動建立新的 <xref:System.Activities.Statements.Sequence> 活動是 [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 的新功能。  
  
20. 設定**至**屬性<xref:System.Activities.Statements.Assign>活動**索引**。 設定**值**屬性**指派**活動**index + 1**。  
  
 自訂**MyForEach**活動將會立即叫用針對傳遞到它透過每個值執行一次任意活動**項目**集合，做為活動的輸入集合中的值。  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動  
  
1.  建置專案時按**Ctrl + Shift + B**。  
  
2.  在**方案總管 中**，開啟**Workflow1.xaml**設計工具中。  
  
3.  拖曳**MyForEach**活動從工具箱拖曳至設計工具介面。 活動將會在工具箱的區段中，名稱與專案的名稱相同。  
  
4.  設定**項目**屬性**MyForEach**活動**新 Object [] {1，"abc"}**。  
  
5.  拖曳<xref:System.Activities.Statements.WriteLine>活動從**基本型別**工具箱的區段**委派： 主體**區段**MyForEach**活動。  
  
6.  設定**文字**屬性<xref:System.Activities.Statements.WriteLine>活動**Argument.ToString()**。  
  
 當執行工作流程時，主控台將顯示以下資訊：  
  
 **1**   
**abc**