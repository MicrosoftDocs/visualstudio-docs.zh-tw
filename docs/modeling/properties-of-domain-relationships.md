---
title: 網域關聯性的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2de06e33b26f7af66dc0670193561758c5fa5896
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544153"
---
# <a name="properties-of-domain-relationships"></a>網域關聯性的屬性
下表中的屬性會與網域關聯性相關聯。 如需網域關聯性的詳細資訊，請參閱[瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|網域關聯性的存取層級（ `public` 或 `internal` ）。|`public`|
|自訂屬性|用來將屬性加入至從網域關聯性產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|有自訂的函數|如果為 `True` ，表示原始程式碼中提供了自訂的程式碼。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述從網域關聯性（或）產生之原始程式碼類別的繼承種類 `none` `abstract` `sealed` 。|\<none>|
|允許重複|如果為 `True` ，則可以在相同的兩個元素之間建立網域關聯性的重複連結。|`False`|
|基底關聯性|如果網域關聯性是衍生的，則為網域關聯性的基底關聯性。|\<none>|
|為內嵌|如果 `True` 為，則網域關聯性為內嵌關聯性。 如果 `False` 為，則關聯性為參考關聯性。|\<both>|
|名稱|網域關聯性的名稱。|目前名稱|
|命名空間|與網域關聯性關聯的命名空間。|目前的命名空間|
|注意|與網域關聯性相關聯的非正式附注。|\<none>|
|描述|用來記載程式碼，並在產生的設計工具的 UI 中使用的描述。|\<none>|
|顯示名稱|針對網域關聯性產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|選擇性關鍵字，用來為網域關聯性的 F1 說明編制索引。|\<none>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)