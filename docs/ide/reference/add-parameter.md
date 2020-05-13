---
title: 將參數新增至方法的快速動作
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595861"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>使用快速動作將參數新增至方法

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 允許您依使用量而定，自動將參數新增至方法。

**時機：** 您必須將參數新增至方法，並想要自動正確地宣告它。

**原因：** 您可以在呼叫參數之前，將參數新增至方法宣告中，但是此功能會根據方法呼叫自動新增參數。

## <a name="how-to-use-it"></a>如何使用它

1. 為方法呼叫新增額外的引數。

   紅色波浪形顯示在調用該方法的方法的名稱下。

2. 將指標放在紅色波浪上，直到出現"快速操作"功能表。 選取 [快速動作] 功能表上的**向下鍵**，然後選取 [將參數新增至 [方法]]****。

   ![在 Visual Studio 中將參數新增至方法快速動作](media/add-parameter-to-method.png)

   > [!TIP]
   > 您還可以通過將游標放在方法調用的行上，然後按**Ctrl**+來訪問"快速操作"功能表 **。** （期間）或選擇檔邊距中的燈泡圖示。

   Visual Studio 會將新參數新增至方法宣告中。

> [!NOTE]
> 如果您對該方法有其他呼叫，則在使用這個快速動作後，它們可能會產生錯誤，因為它們沒有為新增的參數指定引數。

## <a name="see-also"></a>另請參閱

- [將參數新增至建構函式](generate-constructor.md#addparameter)
