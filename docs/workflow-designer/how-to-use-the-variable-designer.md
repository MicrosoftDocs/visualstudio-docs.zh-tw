---
title: 工作流程設計工具-如何： 使用變數設計工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc180df4a9be83c0f0b755bffd7ed40009b41497
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970095"
---
# <a name="how-to-use-the-variable-designer"></a>HOW TO：使用變數設計工具

變數設計工具適用於建立變數，以用於資料繫結的狀況以及條件陳述式。 按一下即可存取設計工具**變數**設計畫布左下角的按鈕。 設計工具會包含一份表格顯示並可依每個資料行標頭，除了變數**預設**資料行。 每個變數都會包含名稱、變數型別、範圍與預設值 (如果有的話)。 名稱和預設值都是可編輯的文字欄位，而型別和範圍都可從下拉式清單中選取。 範圍是叫用變數設計工具時選取的活動。 如果無法在選取範圍內建立變數，則範圍會預設為離選取最近的祖系活動，以便在其範圍內建立變數。 如需詳細資訊，請參閱[變數和引數 (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

 直到使用者明確使用其中一種排序控制項、關閉與重新開啟變數設計工具，或建立其他變數為止，排序不會套用。

## <a name="to-create-a-new-variable"></a>若要建立新變數

1.  Visual Studio 中開啟工作流程或活動的方案。

2.  在設計畫布上，選取工作流程中的活動。

3.  開啟變數設計工具，依序按一下**變數**設計畫布左下角的按鈕。 變數設計工具隨即出現。

4.  按一下空白的資料列標示為**建立變數**。 這會新增新的資料列與新的變數，使用下列預設值： 的 variablex**名稱**其中 x 是整數，其初始值為 1，會自動遞增以建立唯一的變數名稱， **字串**如**變數型別**，和**順序**如**範圍**。 不加入任何值**預設**。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除變數，按一下以選取變數，並按一下**刪除**索引鍵。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [如何：使用引數設計工具](../workflow-designer/how-to-use-the-argument-designer.md)