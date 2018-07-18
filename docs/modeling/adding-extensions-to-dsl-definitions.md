---
title: 在 DSL 定義中加入擴充功能
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947530"
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL 定義中加入擴充功能

DSL 定義延伸模組可讓您建立擴充功能的網域特定定義域語言 (DSL) 來封裝。 DSL 擴充功能，包含在 Visual Studio 整合擴充功能 (VSIX)，可以在使用者的電腦上安裝在 DSL 相同的方式。 額外的功能可以動態啟用和停用在執行階段。 Dsl 不必明確設計用於擴充功能，並擴充功能可以設計成第三方，或更新版本中，而不會變更延伸的 DSL。

DSL 延伸模組可以包含下列功能：

-   模型和呈現項目的屬性

-   裝飾項目圖形和連接器

-   類別、 關聯性、 圖形和連接器

-   驗證條件約束

-   工具箱項目和索引標籤

擴充的 DSL 的使用者可以建立和儲存模型，其中包含的其他功能的執行個體。 模型可以讀取由其他使用者已安裝適當的副檔名。 尚未安裝擴充功能的使用者無法使用額外的功能，但也可以更新儲存模型，而不會遺失的其他功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱

- [相關部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
