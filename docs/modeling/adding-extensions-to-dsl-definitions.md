---
title: 在 DSL 定義中加入擴充功能
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5c02fc28e7ffec4765d94758c838ab149e7ac3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064189"
---
# <a name="add-extensions-to-dsl-definitions"></a>在 DSL 定義中新增延伸模組

DSL 定義延伸模組可讓您建立的特定領域語言 (DSL) 延伸模組套件。 DSL 的延伸模組，其包含在 Visual Studio 整合擴充功能 (VSIX)，可以安裝在使用者的電腦，做為 DSL 相同的方式。 額外的功能可動態啟用及停用在執行階段。 不需要針對延伸模組，明確設計 Dsl 和擴充功能可以設計成更新版本中，或由協力廠商沒有改變擴充的 DSL。

DSL 延伸模組可以包含下列功能：

- 模型和呈現項目的屬性

- 圖案和接點的裝飾項目

- 類別、 關聯性、 圖形和連接器

- 驗證條件約束

- 工具箱項目和索引標籤

擴充 DSL 的使用者可以建立及儲存模型，包含其他功能的執行個體。 已安裝適當的延伸模組的其他使用者可以讀取模型。 尚未安裝擴充功能的使用者無法使用額外的功能，但是它們可以更新，並儲存模型，而不會遺失的其他功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱

- [相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
