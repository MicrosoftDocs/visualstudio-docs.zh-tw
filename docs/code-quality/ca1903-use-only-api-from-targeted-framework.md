---
title: CA1903：只使用來自目標架構的 API
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4f49c8a4da3ad746e5221bb689285c89d48e6e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918555"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903：只使用來自目標架構的 API
|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|分類|Microsoft.Portability|
|中斷變更|-針對外部可見成員或類型的簽章引發時中斷。<br /><br /> 非中斷-時引發的方法主體中。|

## <a name="cause"></a>原因
 成員或類型成員或類型使用不含專案的目標 framework 的 service pack 中導入。

## <a name="rule-description"></a>規則描述
 .NET Framework 2.0 Service Pack 1 和 2，.NET Framework 3.0 Service Pack 1 和 2 和.NET Framework 3.5 Service Pack 1 已包含新成員和類型。 .NET framework 的主要版本為目標的專案不小心可能需要相依於這些新的 Api。 若要避免這種相依性，此規則會引發任何新成員和預設專案的目標 framework 未包含的類型的用法。

 **目標 Framework 和服務組件相依性**

|||
|-|-|
|當目標 framework 是|中導入的成員的用法時引發|
|.NET Framework 2.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2，.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 若要變更專案的目標 framework，請參閱[以特定的.NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要移除的服務組件的相依性，移除所有的使用方式之新成員的類型。 如果這是刻意的相依性，請隱藏警告或關閉這個規則。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果這不是刻意相依於指定的服務組件，請勿隱藏此規則的警告。 在此情況下，您的應用程式可能無法在系統上執行未安裝此 service pack。 隱藏警告或關閉這項規則如果這是刻意的相依性。

## <a name="example"></a>範例
 下列範例會使用型別僅供以.NET 2.0 Service Pack 1 的 DateTimeOffset 的類別。 這個範例需要在專案屬性中的目標 Framework 下拉式清單中已選取 .NET Framework 2.0。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>範例
 下列範例會將先前所述的違規修正 DateTime 型別取代成 DateTimeOffset 類型的用法。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>另請參閱
 [可攜性警告](../code-quality/portability-warnings.md)[以特定的.NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)