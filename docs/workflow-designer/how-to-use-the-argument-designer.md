---
title: 工作流程設計工具-如何：使用引數設計工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e73dcd167f6f267c7979f5c3ffb806b9f12d534a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891559"
---
# <a name="how-to-use-the-argument-designer"></a>HOW TO：使用引數設計工具

相較於舊版的.NET Framework，引數設計工具可讓您輕鬆地讓資料流入及流出活動。 按一下即可存取設計工具**引數**設計畫布左下角的按鈕。 設計工具會包含一份表格顯示，並可依每個資料行標頭中，除了引數**預設值**資料行。 每個引數都包含名稱、in/out/in-out/屬性方向、型別與預設運算式值 (如果有的話)。 名稱與預設運算式值都是可編輯的文字欄位，而型別和方向都可從下拉式清單中選取。 如需詳細資訊，請參閱 <<c0> [ 變數和引數 (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

## <a name="to-create-a-new-argument"></a>若要建立新引數

1.  Visual Studio 中開啟工作流程或活動的解決方案。

2.  開啟 [引數設計工具]，請依序按一下**引數**設計畫布左下角的按鈕。 引數設計工具隨即出現。

3.  按一下標示為空白資料列**建立引數**。 這會將新的資料列新增使用新的引數，使用下列的預設值： 針對 argumentx**名稱**其中 x 是整數，其初始值為 1，會自動遞增以建立唯一的引數名稱**中** for**方向**，和**字串**如**引數型別**。 不加入任何值**預設值**。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除引數，選取引數依序按一下它，然後按**刪除**索引鍵。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)