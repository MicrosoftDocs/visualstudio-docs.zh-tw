---
title: 使用 Lambda 運算式或區塊主體
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531925"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>為 Lambda 運算式使用運算式主體或區塊主體

此重構適用於：

- C#

**功能：** 可讓您重構 Lambda 運算式以使用運算式主體或區塊主體。

**時機：** 您偏好以 Lambda 運算式使用運算式主體或區塊主體。

**原因：** Lambda 運算式可以根據您的使用者喜好設定來進行重構，以改善可讀性。

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda 運算式主體或區塊主體重構

1. 將游標放在 Lambda 運算子的右側。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

  ![使用 Lambda 運算式/區塊主體](media/block-body-lambda.png)

3. 選取 [為 Lambda 運算式使用區塊主體] 或 [為 Lambda 運算式使用運算式主體]。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)