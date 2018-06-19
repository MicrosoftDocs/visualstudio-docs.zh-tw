---
title: 工作流程設計工具-如何： 使用引數設計工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94656c7242c4bc6bc1dd1430230dac62a5322f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971868"
---
# <a name="how-to-use-the-argument-designer"></a>HOW TO：使用引數設計工具

相較於舊版.NET Framework，引數設計工具可讓您輕鬆地讓資料流入及流出活動。 按一下即可存取設計工具**引數**設計畫布左下角的按鈕。 設計工具會包含引數出現在表格形式，而且可依每個資料行標頭，除了清單**預設值**資料行。 每個引數都包含名稱、in/out/in-out/屬性方向、型別與預設運算式值 (如果有的話)。 名稱與預設運算式值都是可編輯的文字欄位，而型別和方向都可從下拉式清單中選取。 如需詳細資訊，請參閱[變數和引數 (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

## <a name="to-create-a-new-argument"></a>若要建立新引數

1.  Visual Studio 2010 中開啟工作流程或活動的方案。

2.  開啟引數設計工具，依序按一下**引數**設計畫布左下角的按鈕。 引數設計工具隨即出現。

3.  按一下空白的資料列標示為**建立引數**。 這會新增新的資料列與新的引數，使用下列預設值： 針對 argumentx**名稱**其中 x 是整數，其初始值為 1，會自動遞增以建立唯一引數名稱**中**如**方向**，和**字串**如**引數型別**。 不加入任何值**預設值**。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除引數，選取引數依序按一下它，然後按**刪除**索引鍵。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)