---
title: "網域類別的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f6e7310f88b4c5f0855a6851219727ae0dc82d86
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
網域類別具有下表中的屬性。 網域類別的詳細資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|  
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個網域類別產生。|\<none>|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|繼承修飾詞|描述來源的程式碼類別產生的網域類別的繼承種類 (`none`，`abstract`或`sealed`)。|`none`|  
|基底類別|如果此網域類別衍生，基底類別的名稱。|\<none>|  
|名稱|這個網域類別的名稱。|目前的名稱|  
|命名空間|這個網域類別的命名空間。|目前的命名空間|  
|注意|與這個網域類別相關聯的非正式附註。|\<none>|  
|描述|描述用來產生的設計工具的 UI 的文件。|\<none>|  
|顯示名稱|會產生這個網域類別設計工具中顯示的名稱。|\<none>|  
|說明關鍵字|選擇性的關鍵字是用來編製索引的這個網域類別的 F1 說明。|\<none>|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)