---
title: "CA1030： 建議在適當時使用事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 616c79e67662407562f735f5cddd2c0bf2796797
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030：建議在適當時使用事件
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 Public、 protected 或 private 方法名稱開頭為下列其中一項：  
  
-   附加元件  
  
-   RemoveOn  
  
-   引發  
  
-   引發  
  
## <a name="rule-description"></a>規則描述  
 此規則會偵測具有事件常用名稱的方法。 事件遵循觀察者 」 或 「 發行-訂閱設計模式;一個物件的狀態變更必須傳送到其他物件時，會使用這些項目。 如果呼叫的方法，取得回應清楚定義的狀態變更，此方法應叫用事件處理常式。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。  
  
 使用者介面應用程式，其中使用者動作，例如按一下按鈕會使要執行的程式碼區段中，找到事件的一些常見的範例。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型並不限於使用者介面，則它應該用於您必須進行通訊狀態會變更為一個或多個物件的任何地方。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 如果物件的狀態變更時，所呼叫的方法，您應該考慮變更設計，以利用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果該方法不適用於隱藏此規則的警告[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型。