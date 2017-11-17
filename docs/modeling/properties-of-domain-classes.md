---
title: "網域類別的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e9bed31caa63a12677e7b9798e6cf72524500c21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-classes"></a>網域類別的屬性
網域類別具有下表中的屬性。 網域類別的詳細資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|說明|預設|  
|--------------|-----------------|-------------|  
|存取修飾詞|網域類別的存取層級 (`public` 或 `internal`)。|`public`|  
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個網域類別產生。|\<無 >|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|繼承修飾詞|描述來源的程式碼類別產生的網域類別的繼承種類 (`none`，`abstract`或`sealed`)。|`none`|  
|基底類別|如果此網域類別衍生，基底類別的名稱。|\<無 >|  
|名稱|這個網域類別的名稱。|目前的名稱|  
|命名空間|這個網域類別的命名空間。|目前的命名空間|  
|注意|與這個網域類別相關聯的非正式附註。|\<無 >|  
|說明|描述用來產生的設計工具的 UI 的文件。|\<無 >|  
|顯示名稱|會產生這個網域類別設計工具中顯示的名稱。|\<無 >|  
|說明關鍵字|選擇性的關鍵字是用來編製索引的這個網域類別的 F1 說明。|\<無 >|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)