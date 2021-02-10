---
title: 網域角色的屬性
description: 瞭解與網域角色相關聯的屬性，例如集合類型、代理商屬性，以及屬性可流覽。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9edee5f8128933b2ecb36434a64d39c40d3d799f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941303"
---
# <a name="properties-of-domain-roles"></a>網域角色的屬性
下表中的屬性與網域角色相關聯。 如需有關網域角色的詳細資訊，請參閱 [瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

|屬性|描述|預設|
|-|-|-|
|集合類型|如果此角色的多重性為 0 .. * 或 1 \* ，則這個屬性會自訂用來儲存連結集合的泛型型別。|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 使用|
|自訂屬性|您在此指定的屬性將會新增為產生的程式碼類別的屬性。|<無\>|
|是可流覽的屬性|如果為 `True` ，而且如果關聯性的多重性是 0 ..1 或 1 ..1，使用者就可以在 [ **屬性** ] 視窗中流覽角色屬性。 屬性會顯示關聯性連結另一端的元素名稱。|`True`|
|為屬性產生器|如果為，則會為 `True` 此角色產生角色屬性，您可以使用此屬性來跨越程式碼中的關聯性。 如果您將此設定為 false，則可以使用網域關聯性的靜態方法，以較不有效率的方式來進行關聯性。|`True`|
|屬性 Getter 存取修飾詞|產生的屬性之 getter 的存取修飾詞 (`public` 、、 `internal` `private` 、 `protected` 或 `protected internal`) 。|`public`|
|屬性 Setter 存取修飾詞|產生的屬性之 setter 的存取修飾詞 (`public` 、、 `internal` `private` 、 `protected` 或 `protected internal`) 。|`public`|
|多重性|可以播放相反角色 (`0..1` 、 `1..1` 、 `0..*` 或) 的模型元素數目 `1..*` 。 如果多重性為 `0..*` 或 `1..*` ，則產生的屬性工作表示集合，否則產生的屬性工作表示單一模型元素。|相依于關聯性類型，以及這是否為關聯性中的來源或目標角色。|
|名稱|網域角色的名稱。 這個屬性不能包含空格。|此角色之角色扮演者的網域類別名稱。|
|傳播複本|`DoNotPropagateCopy` -複製的角色扮演者將不會有此連結的複本。<br /><br /> `PropagateCopyToLinkOnly` -複製的連結指向現有的相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -複製的連結指向相對角色扮演者的複本。|`PropagateCopyToLinkAndOppositeRolePlayer` 適用于內嵌的來源角色。<br /><br /> `DoNotPropagateCopy` 適用于其他角色。<br /><br /> 如需詳細資訊，請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)|
|傳播刪除|`True` 刪除相關聯的連結時，刪除扮演此角色的元素。|`True` 適用于嵌入角色的目標。<br /><br /> `False` 適用于其他角色。|
|屬性名稱|角色扮演者程式碼中產生的屬性名稱。 此名稱不能包含空格。|如果此角色有零對一或一對一多重性，則為相反角色的名稱;否則為相反角色的複數化名稱。|
|角色扮演者|可以在關聯性中扮演此角色之專案的網域類別。 這是唯讀的屬性。|此角色之角色扮演者的網域類別。|
|備註|與網域角色相關聯的非正式附注。|<無\>|
|類別|在產生的設計工具中，產生的屬性會出現在 [ **屬性** ] 視窗中的分類。 如果這個屬性是空的，則產生的屬性會出現在 [ **其他** ] 類別之下。|<無\>|
|Description|用來記錄程式碼的描述，用於產生之設計工具的 UI 中。<br /><br /> 此描述會出現在「角色扮演者」類別上產生之屬性的 IntelliSense 工具提示中。|`Description for`*角色的完整名稱*|
|顯示名稱|針對網域角色所產生的設計工具中顯示的名稱。|Name 屬性的調整值。|
|說明關鍵字|選擇性的關鍵字，用來為網域角色的 F1 說明編制索引。|\<none>|
|屬性顯示名稱|產生的角色屬性在產生的設計工具中顯示的名稱。|[屬性名稱] 屬性的調整值。|

> [!NOTE]
> 顯示名稱的預設值是以相關聯的屬性值為基礎，方法是在前面加上小寫字元的每個大寫字元之前插入空格，而不是在後面加上另一個大寫字元。

## <a name="see-also"></a>另請參閱

- [網域關聯性的屬性](../modeling/properties-of-domain-relationships.md)