---
title: 網域類別的屬性
description: 瞭解網域類別的各種屬性，例如存取修飾詞、自訂屬性，以及產生雙重衍生。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc86f04841a819423bc45c9220d6de80a5340b2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916002"
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
網域類別具有下表中的屬性。 如需網域類別的詳細資訊，請參閱 [瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|
|自訂屬性|用來將屬性新增至從這個網域類別產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫進行自訂) 。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂的函式|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述從網域類別產生之原始程式碼類別的繼承類型 (`none` `abstract` 或 `sealed`) 。|`none`|
|基類|如果衍生這個網域類別，則為基類的名稱。|\<none>|
|名稱|這個網域類別的名稱。|目前的名稱|
|命名空間|這個網域類別的命名空間。|目前的命名空間|
|備註|與此網域類別相關聯的非正式附注。|\<none>|
|Description|用來記錄所產生設計工具 UI 的描述。|\<none>|
|顯示名稱|將在為這個網域類別產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|選擇性的關鍵字，用來為這個網域類別的 F1 說明編制索引。|\<none>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)