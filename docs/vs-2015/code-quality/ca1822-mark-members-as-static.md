---
title: CA1822： 將成員標記為靜態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7b85d12038d4c505f912dd2f9440829f2c80679c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183491"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822：將成員標記為靜態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱 < [CA1822： 將成員標記為靜態](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static)docs.microsoft.com 上。  
  
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷-成員不是組件外部可見不論有變更您進行。 非中斷-如果您只要變更成員的執行個體成員為`this`關鍵字。<br /><br /> 中斷-如果您將成員從執行個體成員變更為靜態成員，而且它是組件外部可見。|  
  
## <a name="cause"></a>原因  
 不會存取執行個體資料成員未標記為 static (在中共用[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])。  
  
## <a name="rule-description"></a>規則描述  
 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 發出非虛擬呼叫站台，可防止在每個呼叫，以確保目前的物件指標為非 null 的執行階段檢查。 這能夠獲得可觀的效能是重視效能的程式碼。 在某些情況下，無法存取目前的物件執行個體就表示正確性發生問題。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 將標示為靜態成員 (中或共用[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 或使用 'this '/' Me' 在方法主體，如果適用的話。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可安全地隱藏此規則，先前隨附的程式碼修正會是一項重大變更的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)

