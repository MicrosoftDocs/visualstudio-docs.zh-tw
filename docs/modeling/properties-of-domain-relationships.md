---
title: 網域關聯性的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2693994c9ead711f3bb536d0e37f485bc00047b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998917"
---
# <a name="properties-of-domain-relationships"></a>網域關聯性的屬性
下表中的屬性會與網域關聯性相關聯。 網域關聯性的相關資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|網域關聯性的存取層級 (`public`或`internal`)。|`public`|
|自訂屬性|用來將屬性加入至產生自網域關聯性來源的程式碼類別。|\<無>|
|產生雙衍生|如果`True`，產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂建構函式|如果`True`，指出在原始程式碼中已提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述產生自網域關聯性來源的程式碼類別繼承的類型 (`none`，`abstract`或`sealed`)。|\<無>|
|允許重複的項目|如果`True`，重複的網域關聯性的連結可能會建立相同的兩個項目之間。|`False`|
|基底關聯性|如果網域關聯性衍生，基底網域關聯性的關聯性。|\<無>|
|內嵌|如果`True`，網域關聯性是內嵌關聯性。 如果`False`，關聯性是參考關聯性。|\<both>|
|名稱|網域關聯性的名稱。|目前的名稱|
|命名空間|是屬於網域關聯性的命名空間。|目前的命名空間|
|注意|網域關聯性相關聯的非正式附註。|\<無>|
|描述|描述用來記錄程式碼，並會在產生的設計工具的 UI。|\<無>|
|顯示名稱|顯示網域關聯性產生的設計工具中的名稱。|\<無>|
|說明關鍵字|選擇性的關鍵字是用來編製索引的網域關聯性的 F1 說明。|\<無>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)