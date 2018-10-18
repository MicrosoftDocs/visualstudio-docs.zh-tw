---
title: 網域關聯性的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 48af74aa470f195c1cfbd49ffbabb37e2461251d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263727"
---
# <a name="properties-of-domain-relationships"></a>網域關聯性的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下表中的屬性會與網域關聯性相關聯。 網域關聯性的相關資訊，請參閱[了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|存取修飾詞|網域關聯性的存取層級 (`public`或`internal`)。|`public`|  
|自訂屬性|用來將屬性加入至產生自網域關聯性來源的程式碼類別。|\<無 >|  
|產生雙衍生|如果`True`，產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自訂建構函式|如果`True`，指出在原始程式碼中已提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|繼承修飾詞|描述產生自網域關聯性來源的程式碼類別繼承的類型 (`none`，`abstract`或`sealed`)。|\<無 >|  
|允許重複的項目|如果`True`，重複的網域關聯性的連結可能會建立相同的兩個項目之間。|`False`|  
|基底關聯性|如果網域關聯性衍生，基底網域關聯性的關聯性。|\<無 >|  
|內嵌|如果`True`，網域關聯性是內嵌關聯性。 如果`False`，關聯性是參考關聯性。|\<兩者 >|  
|名稱|網域關聯性的名稱。|目前的名稱|  
|命名空間|是屬於網域關聯性的命名空間。|目前的命名空間|  
|注意|網域關聯性相關聯的非正式附註。|\<無 >|  
|描述|描述用來記錄程式碼，並會在產生的設計工具的 UI。|\<無 >|  
|顯示名稱|顯示網域關聯性產生的設計工具中的名稱。|\<無 >|  
|說明關鍵字|選擇性的關鍵字是用來編製索引的網域關聯性的 F1 說明。|\<無 >|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



