---
title: CA1903:只使用來自目標架構的 API
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e57607cdfa8790c9b9fd4e692956f7bb823981a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744862"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903:只使用來自目標架構的 API

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|分類|Microsoft.Portability|
|中斷變更|中斷-時引發的外部可見的成員或型別，簽章。<br /><br /> 非分行-時引發的方法主體中。|

## <a name="cause"></a>原因
 成員或型別使用成員或並未包含在專案的目標 framework 的 service pack 中所導入的類型。

## <a name="rule-description"></a>規則描述
 在.NET Framework 2.0 Service Pack 1 和 2，.NET Framework 3.0 Service Pack 1 和 2 和.NET Framework 3.5 Service Pack 1 中包含新的成員和類型。 以.NET Framework 的主要版本為目標的專案不小心可能需要依賴這些新的 Api。 若要避免此相依性，都會引發此規則使用任何的方式新的成員和預設專案的目標 framework 未包含的類型。

 **目標 Framework 」 和 「 服務組件相依性**

|||
|-|-|
|目標 framework 時|中導入的成員的用法，就會引發|
|.NET Framework 2.0|.NET framework 2.0 SP1，.NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 若要變更專案的目標架構，請參閱[How to:目標的.NET 版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要移除的相依性的 service pack，請移除新的成員或類型的所有使用方式。 如果這是刻意的相依性時，隱藏警告，或關閉這項規則。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果這不是刻意的相依性，於指定的服務組件，則請勿隱藏此規則的警告。 在此情況下，您的應用程式可能無法在系統上執行未安裝此 service pack。 隱藏警告，或關閉這項規則，如果這是刻意的相依性。

## <a name="example"></a>範例
 下列範例顯示使用的型別 DateTimeOffset，僅供以.NET 2.0 Service Pack 1 的類別。 這個範例需要在目標 Framework 下拉式清單中，在專案屬性中已選取 .NET Framework 2.0。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>範例
 下列範例會將先前所述的違規修正 DateTimeOffset 類型的使用方式取代成日期時間型別。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>另請參閱

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)