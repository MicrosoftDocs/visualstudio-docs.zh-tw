---
title: 工作流程設計工具-如何：使用引數設計工具
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2903c69e3cf50f3ed0392239ee8848a79eb50e20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584552"
---
# <a name="how-to-use-the-argument-designer"></a>HOW TO：使用引數設計工具

引數設計工具可讓您輕鬆地允許資料流程入和流出活動。 按一下設計工具畫布左下角的 [**引數**] 按鈕，即可存取設計工具。 設計工具組含以表格形式出現的引數清單，而且除了 [**預設值**] 資料行以外，可以依每個資料行標頭排序。 每個引數都包含名稱、in/out/in-out/屬性方向、型別與預設運算式值 (如果有的話)。 名稱與預設運算式值都是可編輯的文字欄位，而型別和方向都可從下拉式清單中選取。 如需詳細資訊，請參閱[變數和引數（.net）](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

## <a name="to-create-a-new-argument"></a>若要建立新引數

1. 在 Visual Studio 中開啟工作流程或活動解決方案。

2. 按一下設計工具畫布左下角的 [**引數**] 按鈕，以開啟引數設計工具。 引數設計工具隨即出現。

3. 按一下標示為 [**建立引數**] 的空白資料列。 這會加入新的資料列，其中包含使用下列預設值的新引數： [**名稱**] 的 argumentx，其中 x 是整數，其初始值為1，會自動遞增以建立唯一的引數名稱、**在中**為**方向**，以及**引數類型**的**字串**。 **預設值**不會加入任何值。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除引數，請按一下引數加以選取，然後按下**delete**鍵。

## <a name="see-also"></a>請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
