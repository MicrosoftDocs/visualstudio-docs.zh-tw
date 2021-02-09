---
title: 工作流程設計工具-如何：使用引數設計工具
description: 瞭解引數設計工具，以及如何使用引數設計工具來允許資料流程入及流出活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9b97368a942747046aa7641771f84a9f2ed41e11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894097"
---
# <a name="how-to-use-the-argument-designer"></a>HOW TO：使用引數設計工具

引數設計工具可讓您輕鬆地將資料流程入和流出活動。 按一下設計工具畫布左下角的 [ **引數** ] 按鈕，即可存取設計工具。 設計工具會包含以表格形式顯示的引數清單，並可依每個資料行標頭排序，但 **預設值** 資料行除外。 每個引數都包含名稱、in/out/in-out/屬性方向、型別與預設運算式值 (如果有的話)。 名稱與預設運算式值都是可編輯的文字欄位，而型別和方向都可從下拉式清單中選取。 如需詳細資訊，請參閱 [ ( .net) 的變數和引數 ](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)。

## <a name="to-create-a-new-argument"></a>若要建立新引數

1. 在 Visual Studio 中開啟工作流程或活動解決方案。

2. 按一下設計工具畫布左下角的 [ **引數** ] 按鈕，以開啟引數設計工具。 引數設計工具隨即出現。

3. 按一下標示為 [ **建立引數**] 的空資料列。 這會加入新的資料列，其中包含使用下列預設值的新引數： argumentx 的 **名稱**，其中 x 是值為1的 **整數，會** 自動遞增以建立唯一的引數名稱，而針對 **方向**，則是 **引數型** 別的 **字串**。 **預設值** 不會加入任何值。 在工作流程設計過程中，您隨時可以變更這些值。

    > [!NOTE]
    > 若要刪除引數，請按一下引數，然後按下 **delete** 鍵，以選取該引數。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [變數與引數](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
