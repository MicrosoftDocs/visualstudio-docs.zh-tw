---
title: 網域角色的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6dc3f92bf1f9788f501b96540b35006ff112267b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497437"
---
# <a name="properties-of-domain-roles"></a>網域角色的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[屬性的網域角色](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-roles)。  
  
下表中的屬性會與網域角色相關聯。 網域角色的相關資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|集合類型|如果此角色的多重性是 0..* 或 1..\*，這個屬性自訂泛型型別是用來儲存連結的集合。|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 使用|  
|自訂屬性|您在此處指定的屬性會加入做為屬性，產生的程式碼類別。|\<無 >|  
|是可瀏覽屬性嗎|如果`True`，以及角色屬性關聯性的多重性是 0..1 或 1..1，如果可在使用者瀏覽**屬性**視窗。 屬性會顯示在另一端的關聯性連結項目的名稱。|`True`|  
|是屬性產生器|如果`True`，對於此角色，您可以使用來周遊關聯性中的程式碼會產生角色屬性。 如果您設定為 false，您可以比較沒有效率的方式周遊關聯性，使用的網域關聯性的靜態方法。|`True`|  
|屬性 Getter 存取修飾詞|產生的屬性 getter 的存取修飾詞 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|屬性 Setter 存取修飾詞|產生的屬性 setter 的存取修飾詞 (`public`， `internal`， `private`， `protected`，或`protected internal`)。|`public`|  
|多重性|這方面均扮演相反角色的模型項目數目 (`0..1`， `1..1`， `0..*`，或`1..*`)。 如果多重性是 「`0..*`或`1..*`，則產生的屬性代表集合; 否則產生的屬性表示的單一模型項目。|關聯性類型而定，以及是否這是關聯性中的來源或目標角色。|  
|名稱|網域角色的名稱。 這個屬性不能包含空白字元。|此角色的角色扮演者的網域類別名稱。|  
|傳播複本|`DoNotPropagateCopy` -複製的角色扮演者將具有此連結的任何複本。<br /><br /> `PropagateCopyToLinkOnly` -已複製的連結會指向現有的相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -已複製的連結指向一份相反角色扮演者。|`PropagateCopyToLinkAndOppositeRolePlayer` 內嵌的來源角色。<br /><br /> `DoNotPropagateCopy` 其他角色。<br /><br /> 如需詳細資訊，請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)|  
|傳播刪除|`True` 若要刪除的項目刪除相關聯的連結時，扮演此角色。|`True` 內嵌角色的目標。<br /><br /> `False` 其他角色。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 自訂刪除行為](../modeling/customizing-deletion-behavior.md)。|  
|屬性名稱|角色扮演者的程式碼中產生的屬性名稱。 此名稱不能包含空白字元。|如果此角色擁有零對一的相反角色的名稱或一對一的多重性;否則，複數化相反角色的名稱。|  
|角色扮演者|關聯性中扮演此角色的項目網域類別。 這個屬性是唯讀的。|此角色的角色扮演者的網域類別。|  
|注意|網域角色相關聯的非正式附註。|\<無 >|  
|分類|產生的屬性出現在類別目錄**屬性**中產生的設計工具視窗。 如果這個屬性是空的則產生的屬性會出現**Misc**類別|\<無 >|  
|描述|描述用來記錄程式碼，並會在產生的設計工具的 UI。<br /><br /> 描述會出現在角色扮演者類別的產生屬性的 Intellisense 工具提示。|`Description for` *角色的完整名稱*|  
|顯示名稱|網域角色產生的設計工具中顯示名稱。|[名稱] 屬性調整過的值。|  
|說明關鍵字|選擇性的關鍵字是用來編製索引的網域角色的 F1 說明。|\<無 >|  
|內容顯示名稱|會顯示在產生的設計工具產生的角色屬性名稱。|屬性名稱屬性調整過的值。|  
  
> [!NOTE]
>  顯示名稱的預設值根據相關聯的屬性值中，插入小寫字元前面，和另一個大寫字元之後沒有接著，每個大寫字元前的加上空格。  
  
## <a name="see-also"></a>另請參閱  
 [網域關聯性的屬性](../modeling/properties-of-domain-relationships.md)



