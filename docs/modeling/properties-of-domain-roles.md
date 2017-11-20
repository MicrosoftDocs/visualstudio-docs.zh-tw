---
title: "網域角色屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: "9"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e85c47133509e3f7bf7c54b8cfa7f2121a26b04b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-roles"></a>網域角色的屬性
下表中的屬性與相關聯的網域角色。 網域角色的相關資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|說明|預設|  
|--------------|-----------------|-------------|  
|集合型別|如果此角色的重數為 0..* 或 1..\*，這個屬性可自訂用來儲存的連結集合的泛型型別。|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>使用|  
|自訂屬性|您在此處指定的屬性要做為屬性加入至產生的程式碼類別。|< 無\>|  
|是可瀏覽屬性嗎|如果`True`，角色屬性如果 0..1 或 1..1 的關聯性多重性，可在使用者瀏覽和**屬性**視窗。 屬性會顯示在另一端的關聯性連結項目的名稱。|`True`|  
|是屬性產生器|如果`True`，此角色，您可以使用來周遊的關聯性在程式碼中產生角色屬性。 如果您設定為 false，您便可以周遊的關聯性較有效率的方式使用的網域關聯性的靜態方法。|`True`|  
|屬性 Getter 的存取修飾詞|產生的屬性 getter 的存取修飾詞 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|屬性 Setter 的存取修飾詞|產生的屬性 setter 的存取修飾詞 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|多重性|模型項目可以播放相反的角色數目 (`0..1`， `1..1`， `0..*`，或`1..*`)。 如果多重性為`0..*`或`1..*`，則產生的屬性代表集合; 否則產生的屬性表示的單一模型項目。|關聯性類型而定，以及是否這是關聯性中的來源或目標角色。|  
|名稱|網域角色的名稱。 這個屬性不能包含空白字元。|此角色的角色扮演者的領域類別名稱。|  
|傳播複製|`DoNotPropagateCopy`-複製的角色扮演者必須沒有此連結的複本。<br /><br /> `PropagateCopyToLinkOnly`-複製的連結會指向現有的相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-複製的連結會指向相反角色扮演者的複本。|`PropagateCopyToLinkAndOppositeRolePlayer`內嵌來源角色。<br /><br /> `DoNotPropagateCopy`其他角色。<br /><br /> 如需詳細資訊，請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)|  
|傳播刪除|`True`若要刪除的項目相關聯的連結刪除時，扮演此角色。|`True`內嵌的角色的目標。<br /><br /> `False`其他角色。<br /><br /> 如需詳細資訊，請參閱[自訂刪除行為](../modeling/customizing-deletion-behavior.md)。|  
|屬性名稱|角色扮演者的程式碼來產生屬性的名稱。 此名稱不能包含空白字元。|如果此角色擁有零對一的相反角色名稱或一對一的多重性。否則，pluralized 相反的角色名稱。|  
|角色扮演者|項目的領域類別可以在關聯性中扮演此角色。 這個屬性是唯讀的。|角色扮演者，此角色的領域類別。|  
|注意|網域角色相關聯的非正式附註。|< 無\>|  
|分類|產生的屬性出現在類別目錄**屬性**產生的設計工具視窗中。 如果這個屬性是空的則產生的屬性會出現在**其他**類別|< 無\>|  
|說明|描述用來說明程式碼，並使用產生的設計工具的 UI 中。<br /><br /> 描述會出現在 Intellisense 工具提示上的角色 player 類別的產生屬性。|`Description for`*角色的完整名稱*|  
|顯示名稱|顯示產生的網域角色設計工具中的名稱。|Name 屬性調整過的值。|  
|說明關鍵字|選擇性的關鍵字是用來編製索引的網域角色的 F1 說明。|\<無 >|  
|內容顯示名稱|顯示在產生的設計工具產生的角色屬性的名稱。|屬性名稱屬性調整過的值。|  
  
> [!NOTE]
>  相關聯的屬性值為基準的顯示名稱的預設值插入每個大寫字元，而且前面加一個小寫字元，後面沒有接另一個大寫字元之前的空格。  
  
## <a name="see-also"></a>另請參閱  
 [網域關聯性的屬性](../modeling/properties-of-domain-relationships.md)