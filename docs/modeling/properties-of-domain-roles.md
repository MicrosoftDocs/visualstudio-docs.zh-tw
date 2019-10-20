---
title: 網域角色的屬性
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a992cc06a177d329701ca98278ad14632bda8df1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658160"
---
# <a name="properties-of-domain-roles"></a>網域角色的屬性
下表中的屬性會與網域角色相關聯。 如需網域角色的詳細資訊，請參閱[瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|Default|
|-|-|-|
|集合類型|如果此角色的多重性為 0 ... * 或 1.。\*，這個屬性會自訂用來儲存連結集合的泛型型別。|使用 `(none)`  -  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>|
|自訂屬性|您在此處指定的屬性會當做屬性加入至產生的程式碼類別。|< 無 \>|
|是可流覽的屬性|如果 `True`，且關聯性的多重性為 0 ..1 或 1 ..1，則使用者可以在 [**屬性**] 視窗中流覽角色屬性。 屬性會在關聯性連結的另一端顯示元素的名稱。|`True`|
|為屬性產生器|如果 `True`，則會為這個角色產生角色屬性，您可以使用此角色來流覽程式碼中的關聯性。 如果您設定此 false，您可以使用網域關聯性的靜態方法，以較不有效率的方式來流覽關聯性。|`True`|
|屬性 Getter 存取修飾詞|產生的屬性之 getter 的存取修飾詞（`public`、`internal`、`private`、`protected` 或 `protected internal`）。|`public`|
|屬性 Setter 存取修飾詞|產生之屬性（`public`、`internal`、`private`、`protected` 或 `protected internal`）之 setter 的存取修飾詞。|`public`|
|多重性|可以播放相反角色（`0..1`、`1..1`、`0..*` 或 `1..*`）的模型元素數目。 如果 `0..*` 或 `1..*` 多重性，則產生的屬性代表集合;否則，產生的屬性代表單一模型元素。|取決於關聯性類型，以及這是否為關聯性中的來源或目標角色。|
|[屬性]|網域角色的名稱。 這個屬性不能包含空白字元。|此角色之角色扮演者的網域類別名稱。|
|傳播複本|`DoNotPropagateCopy`-複製的角色扮演者將不會有此連結的複本。<br /><br /> `PropagateCopyToLinkOnly`-複製的連結會指向現有的相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-複製的連結會指向相對角色扮演者的複本。|內嵌來源角色的 `PropagateCopyToLinkAndOppositeRolePlayer`。<br /><br /> 適用于其他角色的 `DoNotPropagateCopy`。<br /><br /> 如需詳細資訊，請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)|
|傳播刪除|`True` 在刪除相關聯的連結時，刪除扮演此角色的元素。|嵌入角色的目標 `True`。<br /><br /> 適用于其他角色的 `False`。|
|屬性名稱|角色扮演者的程式碼中產生的屬性名稱。 這個名稱不能包含空白字元。|如果這個角色具有零對一或一對一的多重性，則為相反角色的名稱;否則為相反角色的複數化名稱。|
|角色扮演者|可以在關聯性中扮演此角色之元素的網域類別。 這個屬性是唯讀的。|此角色之角色扮演者的網域類別。|
|備註|與網域角色相關聯的非正式附注。|< 無 \>|
|Category|產生的屬性在產生的設計工具中，出現在 [**屬性**] 視窗中的類別。 如果這個屬性是空的，則產生的屬性會出現在 [**其他**] 類別之下。|< 無 \>|
|描述|用來記載程式碼，並在產生的設計工具的 UI 中使用的描述。<br /><br /> 此描述會出現在角色扮演者類別上產生之屬性的 IntelliSense 工具提示中。|`Description for`*角色的完整名稱*|
|顯示名稱|為網域角色產生的設計工具中顯示的名稱。|Name 屬性的已調整值。|
|說明關鍵字|選擇性關鍵字，用來為網域角色的 F1 說明編制索引。|\<無>|
|屬性顯示名稱|針對產生的角色屬性，在產生的設計工具中顯示的名稱。|屬性名稱屬性的已調整值。|

> [!NOTE]
> 顯示名稱的預設值是以相關聯的屬性值為基礎，方法是在每個大寫字元前面加上小寫字元，而且後面不接著另一個大寫字元。

## <a name="see-also"></a>請參閱

- [網域關聯性的屬性](../modeling/properties-of-domain-relationships.md)