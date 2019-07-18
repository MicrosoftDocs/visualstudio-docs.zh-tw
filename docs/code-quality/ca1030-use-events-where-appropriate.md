---
title: CA1030:建議在適當時使用事件
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a3d2ef30018c7fe57f1e7d728ba1dd152f56f5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714289"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030:建議在適當時使用事件

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

方法名稱開頭為下列其中一項：

- AddOn
- RemoveOn
- 引發
- 引發

根據預設，此規則只會查看外部可見的方法，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

此規則會偵測具有事件常用名稱的方法。 事件遵循觀察者 」 或 「 發行-訂閱設計模式;一個物件的狀態變更告知的其他物件時，會使用這些項目。 取得呼叫的方法，以回應清楚定義的狀態變更，如果此方法應該叫用事件處理常式。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。

其中的使用者動作，例如按一下按鈕會導致一段程式碼執行的使用者介面應用程式中，找到事件的一些常見的範例。 .NET 事件模型不限於使用者介面。 它應該使用任何您必須進行通訊狀態會變更為一個或多個物件的位置。

## <a name="how-to-fix-violations"></a>如何修正違規

如果物件狀態變更時，所呼叫的方法，請考慮變更為使用.NET 事件模式的設計。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果方法無法搭配.NET 事件模型，則隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。
