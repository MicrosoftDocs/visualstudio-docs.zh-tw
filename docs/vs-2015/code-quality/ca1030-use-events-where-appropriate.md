---
title: CA1030： 在適當時使用事件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588472"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030：建議在適當時使用事件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1030： 建議在適當時使用事件](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate)。

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 Public、 protected 或 private 方法名稱開頭為下列其中一項：

-   附加元件

-   RemoveOn

-   引發

-   引發

## <a name="rule-description"></a>規則描述
 此規則會偵測具有事件常用名稱的方法。 事件遵循觀察者 」 或 「 發行-訂閱設計模式;一個物件的狀態變更告知的其他物件時，會使用這些項目。 取得呼叫的方法，以回應清楚定義的狀態變更，如果此方法應該叫用事件處理常式。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。

 其中的使用者動作，例如按一下按鈕會導致一段程式碼執行的使用者介面應用程式中，找到事件的一些常見的範例。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]事件模型並不限於使用者介面，應該用於任何地方您必須進行通訊狀態會變更為一個或多個物件。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果物件狀態變更時，所呼叫的方法，您應該考慮變更設計，以利用[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]事件模型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告，如果方法無法搭配[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]事件模型。



