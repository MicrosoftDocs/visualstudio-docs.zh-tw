---
title: CA2108:必須檢閱實值類型上的宣告式安全性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f4cac83c83b47fda5cf9cde85a3e14d857d2bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545534"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108:必須檢閱實值類型上的宣告式安全性

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

公用或受保護的實值型別會受到[資料與模型化](/dotnet/framework/data/index)或是[連結要求](/dotnet/framework/misc/link-demands)。

## <a name="rule-description"></a>規則描述

配置及其他建構函式執行之前，其預設建構函式來初始化實值型別。 如果實值型別會受到 Demand 或 LinkDemand 的比較，而且呼叫端沒有滿足安全性檢查，而任何建構函式以外的權限預設值將會失敗，並將擲回安全性例外狀況。 實值型別不會取消配置;它會處於其預設建構函式所設定的狀態。 請勿假設呼叫端傳遞實值型別的執行個體具有建立或存取執行個體的權限。

## <a name="how-to-fix-violations"></a>如何修正違規

除非您從類型 中移除安全性檢查，並使用方法層級安全性檢查在其位置中，您無法修正此規則的違規情形。 以這種方式修正違規無法防止具有足夠的權限，無法取得實值型別的執行個體的呼叫端。 您必須確保執行個體的值型別，在其預設狀態下，不會公開機密資訊，且不能用於有害的方式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果任何呼叫端可以取得實值型別，其預設狀態中的執行個體，而不造成安全性威脅，您可以隱藏此規則的警告。

## <a name="example-1"></a>範例 1

下列範例示範包含違反這項規則實值型別程式庫。 `StructureManager`類型會假設呼叫端傳遞實值型別的執行個體具有建立或存取執行個體的權限。

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>範例 2

下列應用程式示範程式庫的弱點。

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

這個範例會產生下列輸出：

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>另請參閱

- [連結要求](/dotnet/framework/misc/link-demands)
- [資料與模型化](/dotnet/framework/data/index)
