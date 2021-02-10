---
title: 定義並取用活動委派
description: 在工作流程設計工具中，瞭解 .NET Framework 4.5 如何包含 InvokeDelegate 活動的現成設計工具，可用來定義及取用活動委派。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 0ce9e59eec2cc9229a5f1104d79337b26115c92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971618"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>HOW TO：定義並取用工作流程設計工具中的活動委派

.NET Framework 4.5 包括活動的現成設計工具 <xref:System.Activities.Statements.InvokeDelegate> 。 這個設計工具可用來將委派指派給衍生自 <xref:System.Activities.ActivityDelegate> 的活動，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

## <a name="define-an-activity-delegate"></a>定義活動委派

1. 建立新的 **工作流程主控台應用程式** 專案。

   > [!NOTE]
   > 如果您沒有看到 **工作流程** 專案範本，請先安裝 Visual Studio 的 **Windows Workflow Foundation** 元件。 如需詳細指示，請參閱 [安裝 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

3. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [**加入**  >  **新專案**]。 選取 [ **工作流程** ] 類別，然後選取 [ **活動** 專案] 範本。 將新活動命名為 **MyForEach** ，然後選取 **[確定]**。

   活動會在工作流程設計工具中開啟。

4. 在 [工作流程設計工具中，按一下 [ **引數** ] 索引標籤。

5. 按一下 **[建立引數]**。 命名新的引數 **專案**。

6. 在 [ **引數類型** ] 資料行中，選取 **[T] 的陣列**。

7. 在類型瀏覽器中，選取 [ **物件** ]，然後選取 **[確定]**。

8. 再次按一下 [ **建立引數** ]。 將新引數命名為 **Body**。 在新引數的 [ **方向** ] 資料行中，選取 [ **屬性**]。

9. 在 [引數類型] 資料行中，選取 **[流覽類型]**

10. 在類型瀏覽器的 [**類型名稱**] 欄位中，輸入 **ActivityAction** 。 在樹狀檢視中選取 [ **ActivityAction \<T>** ]。 在出現的下拉式清單中選取 [**物件**]，以將類型 **ActivityAction \<Object>** 指派給引數。

11. 將 [ <xref:System.Activities.Statements.While> 工具箱] 的 [ **控制流程** ] 區段中的活動拖曳至設計工具介面。

12. 選取 <xref:System.Activities.Statements.While> 活動，然後選取 [ **變數** ] 索引標籤。

13. 選取 [ **建立變數**]。 命名新的變數 **索引**。

14. 在 [ **變數類型** ] 資料行中，選取 [ **Int32**]。 將 **範圍****保持在 [時間]，並** 將 [**預設**] 資料行保留空白。

15. 將活動的 [ **條件** ] 屬性設定 <xref:System.Activities.Statements.While> 為 [ **索引 < 專案]。 [長度];**。

16. 將 <xref:System.Activities.Statements.InvokeDelegate> [工具箱] 的 [ **基本** ] 區段中的活動拖曳至活動的 **主體** <xref:System.Activities.Statements.While> 。

17. 選取 [委派] 下拉式清單中的 [ **主體** ]。

18. 在活動的 [**屬性**] 方格中 <xref:System.Activities.Statements.InvokeDelegate> ，按一下 [**委派引數**] 屬性中的 [ **...** ] 按鈕。

19. 在引數命名 **參數** 的 [**值**] 資料行中，輸入 **Items [Index]**。 按一下 **[確定** ] 以關閉 [ **DelegateArguments** ] 對話方塊。

20. 將 <xref:System.Activities.Statements.Assign> 活動拖曳到 <xref:System.Activities.Statements.InvokeDelegate> 活動底下的水平線上。 系統 <xref:System.Activities.Statements.Assign> 會建立活動，並 <xref:System.Activities.Statements.Sequence> 自動建立活動，以在 **MyForEach** 活動的 [**主體**] 區段中包含這兩個活動。 順序是必要的，因為 **Body** 區段只能包含單一活動。 自動建立新的 <xref:System.Activities.Statements.Sequence> 活動是 .NET Framework 4.5 的新功能。

21. 將活動的 [ **到** ] 屬性設定 <xref:System.Activities.Statements.Assign> 為 [ **索引**]。 將 [**指派**] 活動的 [**值**] 屬性設定為 [**索引 + 1**]。

    自訂 **MyForEach** 活動會針對透過 **Items** 集合傳遞給它的每個值，叫用任意活動一次，並將集合中的值做為活動的輸入。

## <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流程中的自訂活動

1. 按下 **Ctrl** + **Shift** + **B** 以建立專案。

2. 在 **方案總管** 中，在設計工具中開啟 **workflow1.xaml。**

3. 將 [ **MyForEach** ] 活動從 [工具箱] 拖曳至設計工具介面。 活動位於 [工具箱] 的區段中，與專案的名稱相同。

4. 將 **MyForEach** 活動的 **Items** 屬性設為 **new Object [] {1，"abc"}**。

5. 將 [ <xref:System.Activities.Statements.WriteLine> 工具箱] 的 [**基本**] 區段中的活動拖曳至 **MyForEach** 活動的 [**委派： Body** ] 區段。

6. 將活動的 **Text** 屬性設定 <xref:System.Activities.Statements.WriteLine> 為 **( # B1 的引數。**

執行工作流程時，主控台會顯示下列輸出：

**1** 
**abc**
