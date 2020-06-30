---
title: CA1030 建議：適當時使用事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544517"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030:建議在適當時使用事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用、受保護或私用方法名稱的開頭為下列其中一項：

- 項

- RemoveOn

- Fire

- 引發

## <a name="rule-description"></a>規則描述
 此規則會偵測具有事件常用名稱的方法。 事件會遵循觀察者或發行-訂閱設計模式;當某個物件中的狀態變更必須傳達給其他物件時，便會使用它們。 如果呼叫方法以回應清楚定義的狀態變更，則應該由事件處理常式叫用方法。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。

 某些常見的事件範例可在使用者介面應用程式中找到，其中使用者動作（例如按一下按鈕）會導致程式碼區段執行。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]事件模型並不限於使用者介面，您必須在任何地方使用它來傳達一或多個物件的狀態變更。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果在物件的狀態變更時呼叫方法，您應該考慮將設計變更為使用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 事件模型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果方法無法與事件模型搭配使用，請隱藏此規則的警告 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。
