---
title: 網域類別的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b86452d9bfa00c9b107aa0b2748117c64a0384
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747488"
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
網域類別具有下表中的屬性。 如需網域類別的詳細資訊，請參閱[瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|Default|
|-|-|-|
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|
|自訂屬性|用來將屬性（attribute）加入至此網域類別所產生的來來源程式代碼類別。|\<無>|
|產生雙重衍生|如果 `True`，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|有自訂的函數|如果 `True`，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述從網域類別（`none`、`abstract` 或 `sealed`）產生之原始程式碼類別的繼承類型。|`none`|
|基類|如果這個網域類別是衍生的，則為基類的名稱。|\<無>|
|[屬性]|這個網域類別的名稱。|目前名稱|
|命名空間|這個網域類別的命名空間。|目前的命名空間|
|備註|與此網域類別相關聯的非正式附注。|\<無>|
|描述|用來記錄所產生之設計工具 UI 的描述。|\<無>|
|顯示名稱|將顯示在為此網域類別產生的設計工具中的名稱。|\<無>|
|說明關鍵字|選擇性關鍵字，用來為這個網域類別的 F1 說明編制索引。|\<無>|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)