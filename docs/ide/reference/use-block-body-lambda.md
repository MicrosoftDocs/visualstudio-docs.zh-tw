---
title: 使用 Lambda 運算式或區塊主體
description: 瞭解如何使用 [快速動作與重構] 功能表來重構 lambda 運算式，以使用運算式主體或區塊主體。
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bc3b80ad625c58fbe9127978ebc23fd8c764f4d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889898"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>為 Lambda 運算式使用運算式主體或區塊主體

此重構適用於：

- C#

事項 **：** 可讓您重構 lambda 運算式，以使用運算式主體或區塊主體。

時機 **：** 您偏好使用 lambda 運算式來使用運算式主體或區塊主體。

**原因：** 您可以根據使用者喜好設定來重構 Lambda 運算式，以改善可讀性。

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda 運算式主體或區塊主體重構

1. 將游標放在 Lambda 運算子的右側。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

  ![使用 Lambda 運算式/區塊主體](media/block-body-lambda.png)

3. 選取 [為 Lambda 運算式使用區塊主體] 或 [為 Lambda 運算式使用運算式主體]。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)