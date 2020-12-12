---
title: 在 DSL 定義中加入擴充功能
description: 瞭解 DSL 定義延伸模組如何讓您建立延伸模組套件，以 (DSL) 的特定領域語言。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07057c24494a19d77bca872ad87adf20bb125252
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361140"
---
# <a name="add-extensions-to-dsl-definitions"></a>在 DSL 定義中新增延伸模組

DSL 定義延伸模組可讓您建立延伸模組套件，以 (DSL) 的特定領域語言。 DSL 延伸模組（包含在 Visual Studio 整合延伸模組 (VSIX) 中）可以用與 DSL 相同的方式安裝在使用者的電腦上。 您可以在執行時間動態啟用和停用額外的功能。 Dsl 不需要針對擴充功能明確設計，而且擴充功能可以在稍後或由協力廠商設計，而不需要改變擴充的 DSL。

DSL 延伸模組可以包含下列功能：

- Model 和 presentation 元素的屬性

- 圖形和連接器的裝飾專案

- 類別、關聯性、圖形和連接器

- 驗證條件約束

- 工具箱專案和索引標籤

擴充 DSL 的使用者可以建立和儲存包含其他功能實例的模型。 已安裝適當副檔名的其他使用者可以讀取模型。 未安裝此擴充功能的使用者無法使用額外的功能，但可以更新和儲存模型，而不會遺失額外的功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>請參閱

- [相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
