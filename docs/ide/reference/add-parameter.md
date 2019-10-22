---
title: 將參數新增至方法的快速動作
ms.date: 09/28/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d1edc9d38ff4476a9fe76886676bfce1c80a61db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658794"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>使用快速動作將參數新增至方法

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 允許您依使用量而定，自動將參數新增至方法。

**時機：** 您必須將參數新增至方法，並想要自動正確地宣告它。

**原因：** 您可以在呼叫參數之前，將參數新增至方法宣告中，但是此功能會根據方法呼叫自動新增參數。

## <a name="how-to-use-it"></a>如何使用

1. 為方法呼叫新增額外的引數。

   在您呼叫它的方法名稱底下會出現紅色波浪線。

2. 將指標放在紅色曲線上，直到 [快速動作] 功能表出現為止。 選取 [快速動作] 功能表上的**向下鍵**，然後選取 [將參數新增至 [方法]]。

   ![在 Visual Studio 中將參數新增至方法快速動作](media/add-parameter-to-method.png)

   > [!TIP]
   > 您也可以透過將游標放在方法呼叫的行上，然後按 **Ctrl**+ **.** （期間），或選取檔案邊界中的燈泡圖示。

   Visual Studio 會將新參數新增至方法宣告中。

> [!NOTE]
> 如果您對該方法有其他呼叫，則在使用這個快速動作後，它們可能會產生錯誤，因為它們沒有為新增的參數指定引數。

## <a name="see-also"></a>請參閱

- [將參數新增至建構函式](generate-constructor.md#addparameter)