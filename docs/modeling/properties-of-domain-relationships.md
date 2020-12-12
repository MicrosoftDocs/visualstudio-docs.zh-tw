---
title: 網域關聯性的屬性
description: 瞭解與網域 relationshop 相關聯的屬性，例如存取修飾詞、代理商屬性，以及產生雙重衍生。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c5db50432947b99a2667280fe7861e7acd95ac
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362453"
---
# <a name="properties-of-domain-relationships"></a>網域關聯性的屬性
下表中的屬性與網域關聯性相關聯。 如需有關網域關聯性的詳細資訊，請參閱 [瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|網域關聯性的存取層級 (`public` 或 `internal`) 。|`public`|
|自訂屬性|用來將屬性新增至從網域關聯性產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫自訂) 。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂的函式|如果為 `True` ，表示原始程式碼中提供的是自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述從網域關聯性 (或) 產生之原始程式碼類別的繼承類型 `none` `abstract` `sealed` 。|\<none>|
|允許重複|如果為 `True` ，則可能在相同的兩個元素之間建立網域關聯性的重複連結。|`False`|
|基底關聯性|如果衍生的是網域關聯性，則為網域關聯性的基底關聯性。|\<none>|
|正在內嵌|如果 `True` 為，則網域關聯性是內嵌關聯性。 如果 `False` 為，則關聯性是參考關聯性。|\<both>|
|名稱|網域關聯性的名稱。|目前的名稱|
|命名空間|與網域關聯性相關聯的命名空間。|目前的命名空間|
|附註|與網域關聯性相關聯的非正式附注。|\<none>|
|說明|用來記錄程式碼的描述，用於產生之設計工具的 UI 中。|\<none>|
|顯示名稱|針對網域關聯性所產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|選擇性的關鍵字，用來為定義域關聯性的 F1 說明編制索引。|\<none>|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)