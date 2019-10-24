---
title: 在 DSL 定義中加入擴充功能
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3e44c79783479c46247e4026788725d6ae16da7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747647"
---
# <a name="add-extensions-to-dsl-definitions"></a>在 DSL 定義中新增延伸模組

DSL 定義延伸模組可讓您建立特定領域語言（DSL）的延伸套件。 DSL 延伸模組（包含在 Visual Studio 整合擴充功能（VSIX）中）可以使用與 DSL 相同的方式安裝在使用者的電腦上。 這些額外功能可以在執行時間動態啟用及停用。 Dsl 不一定要針對延伸模組進行明確設計，而且延伸模組可以在稍後或由協力廠商設計，而不需要改變擴充的 DSL。

DSL 延伸模組可以包含下列功能：

- Model 和 presentation 元素的屬性

- 圖形和連接器的裝飾專案

- 類別、關聯性、圖形和連接器

- 驗證條件約束

- 工具箱專案和索引標籤

延伸 DSL 的使用者可以建立並儲存包含額外功能實例的模型。 已安裝適當擴充功能的其他使用者可以讀取此模型。 尚未安裝延伸模組的使用者無法使用其他功能，但可以更新並儲存模型，而不會遺失其他功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>請參閱

- [相關的 blog 文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
