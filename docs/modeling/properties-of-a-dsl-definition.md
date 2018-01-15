---
title: "DSL 定義的內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6a3b1dc2966f2fd07c8f0462ebb47bebf25b843c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義的屬性
DslDefinition 屬性會定義*網域特定領域語言*定義屬性，例如版本編號。 DslDefinition 屬性會出現在**屬性**視窗中，當您按一下圖中的開放區域*網域特定語言設計工具*。  
  
 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 DslDefinition 具有下表中的屬性：  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|存取修飾詞|決定網域類別的存取修飾詞為公用或內部。|public|  
|自訂屬性|自訂網域類別的屬性。<br /><br /> **請注意**新增屬性使用瀏覽按鈕。|\<無 >|  
|公司名稱|目前的公司名稱，在系統登錄的名稱。|目前的公司名稱|  
|名稱|這個網域類別的名稱。|目前的名稱|  
|命名空間|命名空間會與此網域類別建立關聯。|目前的命名空間|  
|封裝 Guid|Guid[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|封裝命名空間|命名空間[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|產品名稱|要註冊進行的產品名稱[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|注意|此網域類別相關聯的資訊。|\<無 >|  
|描述|這個網域類別的描述。|\<無 >|  
|顯示名稱|會產生這個網域類別設計工具中顯示的名稱。|\<無 >|  
|說明關鍵字|此網域類別相關聯的 help 關鍵字。|\<無 >|  
|組建|此網域特定領域語言定義累加組建編號。|0|  
|主要版本|此網域特定領域語言定義累加式的主要組建編號。|1|  
|次要版本|此網域特定領域語言定義累加式的次要組建編號。|0|  
|修訂|累加版本建置此網域特定領域語言定義的數字。|0|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)