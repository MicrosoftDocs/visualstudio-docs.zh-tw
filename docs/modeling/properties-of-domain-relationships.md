---
title: 網域關聯性的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 32943d7e40f7ce1a86ab2236862404686a4d922f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-domain-relationships"></a>網域關聯性的屬性
下表中的屬性與相關聯的網域關聯性。 如需網域關係資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|--------------|-----------------|-------------|
|存取修飾詞|領域關聯的存取層級 (`public`或`internal`)。|`public`|
|自訂屬性|用來將屬性加入至產生的網域關聯性來源的程式碼類別。|\<無 >|
|會產生雙衍生|如果`True`，會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂建構函式|如果`True`，表示在原始碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述產生的網域關聯性來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|\<無 >|
|允許重複的項目|如果`True`，重複的網域關聯性的連結可能會建立相同的兩個元素之間。|`False`|
|基底關聯性|如果網域關聯性衍生，基底的關聯性的網域關聯性。|\<無 >|
|為內嵌|如果`True`，網域關聯性是內嵌的關聯性。 如果`False`，關聯性是參考關聯性。|\<同時 >|
|名稱|網域關聯性的名稱。|目前的名稱|
|命名空間|附屬於領域關聯的命名空間。|目前的命名空間|
|注意|非正式的網域關聯性相關聯的資訊。|\<無 >|
|描述|描述用來說明程式碼，並使用產生的設計工具的 UI 中。|\<無 >|
|顯示名稱|顯示產生的網域關聯性設計工具中的名稱。|\<無 >|
|說明關鍵字|選擇性的關鍵字是用來編製索引的網域關聯性的 F1 說明。|\<無 >|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)