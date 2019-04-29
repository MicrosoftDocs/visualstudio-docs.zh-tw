---
title: 網域類別的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb66a0d497c86091f689f119e57a5230f125e8de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999193"
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
網域類別會在下表中的屬性。 網域類別的詳細資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個網域類別產生。|\<無>|
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述的繼承來源的程式碼類別產生自領域類別的類型 (`none`，`abstract`或`sealed`)。|`none`|
|基底類別|如果此網域類別衍生，基底類別的名稱。|\<無>|
|名稱|這個領域類別的名稱。|目前的名稱|
|命名空間|這個領域類別的命名空間。|目前的命名空間|
|注意|與此領域類別相關聯的非正式附註。|\<無>|
|描述|描述用來產生的設計工具的 UI 的文件。|\<無>|
|顯示名稱|將會顯示在這個網域類別產生的設計工具的名稱。|\<無>|
|說明關鍵字|選擇性的關鍵字是用來編製索引的這個網域類別的 F1 說明。|\<無>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)