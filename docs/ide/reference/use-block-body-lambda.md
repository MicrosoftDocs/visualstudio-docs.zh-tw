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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531925"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>為 Lambda 運算式使用運算式主體或區塊主體

此重構適用於：

- C#

**內容：** 允許您重構 lambda 運算式以使用運算式正文或塊體。

**何時：** 您希望 lambda 運算式使用運算式正文或塊正文。

**原因：** 可以重構 Lambda 運算式，以便根據使用者首選項提高可讀性。

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda 運算式主體或區塊主體重構

1. 將游標放在 Lambda 運算子的右側。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

  ![使用 Lambda 運算式/區塊主體](media/block-body-lambda.png)

3. 選取 [為 Lambda 運算式使用區塊主體]**** 或 [為 Lambda 運算式使用運算式主體]****。

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)