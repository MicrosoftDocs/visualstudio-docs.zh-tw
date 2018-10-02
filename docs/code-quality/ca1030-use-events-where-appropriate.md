---
title: CA1030：建議在適當時使用事件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31eb949588353a6f2f11ddbbdf516d1a5da63488
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859728"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030：建議在適當時使用事件
|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 Public、 protected 或 private 方法名稱開頭為下列其中一項：

- 附加元件

- RemoveOn

- 引發

- 引發

## <a name="rule-description"></a>規則描述
 此規則會偵測具有事件常用名稱的方法。 事件遵循觀察者 」 或 「 發行-訂閱設計模式;一個物件的狀態變更告知的其他物件時，會使用這些項目。 取得呼叫的方法，以回應清楚定義的狀態變更，如果此方法應該叫用事件處理常式。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。

 其中的使用者動作，例如按一下按鈕會導致一段程式碼執行的使用者介面應用程式中，找到事件的一些常見的範例。 .NET Framework 事件模型並不限於使用者介面;它應該使用任何您必須進行通訊狀態會變更為一個或多個物件的位置。

## <a name="how-to-fix-violations"></a>如何修正違規
 如果物件狀態變更時，所呼叫的方法，您應該考慮變更為使用.NET Framework 事件模式的設計。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果方法無法搭配.NET Framework 事件模型，則隱藏此規則的警告。