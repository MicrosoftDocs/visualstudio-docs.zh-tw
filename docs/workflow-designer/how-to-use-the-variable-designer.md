---
title: 工作流程設計工具-how to：使用變數設計工具
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59a0da5ad0345ba0733f52d087b262bdc706cd21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650242"
---
# <a name="how-to-use-the-variable-designer"></a>作法：使用變數設計工具

變數設計工具適用於建立變數，以用於資料繫結的狀況以及條件陳述式。 按一下設計工具畫布左下角的 [**變數**] 按鈕，即可存取設計工具。 設計工具組含以表格形式出現的變數清單，而且可以依每個資料行標頭來排序，但**預設**資料行除外。 每個變數都會包含名稱、變數型別、範圍與預設值 (如果有的話)。 名稱和預設值都是可編輯的文字欄位，而型別和範圍都可從下拉式清單中選取。 範圍是叫用變數設計工具時選取的活動。 如果無法在選取範圍內建立變數，則範圍會預設為離選取最近的祖系活動，以便在其範圍內建立變數。 如需詳細資訊，請參閱[變數和引數（.net）](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

 直到使用者明確使用其中一種排序控制項、關閉與重新開啟變數設計工具，或建立其他變數為止，排序不會套用。

## <a name="to-create-a-new-variable"></a>若要建立新變數

1. 在 Visual Studio 中開啟工作流程或活動解決方案。

2. 在設計畫布上，選取工作流程中的活動。

3. 按一下設計工具畫布左下角的 [**變數**] 按鈕，以開啟變數設計工具。 變數設計工具隨即出現。

4. 按一下標示為 [**建立變數**] 的空白資料列。 這會使用下列預設值來加入新的資料列，其中包含新的變數： [**名稱**] 的 variablex，其中 x 是整數，其初始值為1，會自動遞增以建立唯一的變數名稱，為變數**字串** **類型**，以及**範圍**的**順序**。 **預設**不會加入任何值。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除變數，請按一下變數加以選取，然後按下**delete**鍵。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [如何：使用引數設計工具](../workflow-designer/how-to-use-the-argument-designer.md)