---
title: 網域類別的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651999"
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

網域類別具有下表中的屬性。 如需網域類別的詳細資訊，請參閱 [瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|--------------|-----------------|-------------|
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|
|自訂屬性|用來將屬性新增至從這個網域類別產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫進行自訂) 。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|具有自訂的函式|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|
|繼承修飾詞|描述從網域類別產生之原始程式碼類別的繼承類型 (`none` `abstract` 或 `sealed`) 。|`none`|
|基類|如果衍生這個網域類別，則為基類的名稱。|\<none>|
|Name|這個網域類別的名稱。|目前的名稱|
|命名空間|這個網域類別的命名空間。|目前的命名空間|
|備註|與此網域類別相關聯的非正式附注。|\<none>|
|描述|用來記錄所產生設計工具 UI 的描述。|\<none>|
|顯示名稱|將在為這個網域類別產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|選擇性的關鍵字，用來為這個網域類別的 F1 說明編制索引。|\<none>|

## <a name="see-also"></a>另請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
