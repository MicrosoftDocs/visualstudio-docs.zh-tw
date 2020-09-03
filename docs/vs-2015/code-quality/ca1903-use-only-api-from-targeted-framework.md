---
title: CA1903：僅使用來自目標架構的 API |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545245"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903:只使用來自目標架構的 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [CA1903：僅使用來自目標 framework 的 API](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework)。

|Item|值|
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|類別|Microsoft 可攜性|
|中斷變更|重大-針對外部可見成員或類型的簽章引發。<br /><br /> 在方法主體中引發時，不會中斷。|

## <a name="cause"></a>原因
 成員或類型所使用的成員或類型，是在 service pack 中引進，但不包含在專案的目標架構中。

## <a name="rule-description"></a>規則描述
 新成員和類型包含在 .NET Framework 2.0 Service Pack 1 和2、.NET Framework 3.0 Service Pack 1 和2，以及 .NET Framework 3.5 Service Pack 1 中。 以 .NET Framework 的主要版本為目標的專案，可能會不慎依賴這些新的 Api。 若要避免此相依性，此規則會在專案的目標架構預設不包含的任何新成員和類型的使用上引發。

 **目標 Framework 和 Service Pack 相依性**

|Item|值|
|-|-|
|當目標 framework 為|在中導入的成員使用上引發|
|.NET Framework 2.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 若要變更專案的目標架構，請參閱以 [特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要移除 service pack 的相依性，請移除新成員或類型的所有使用方式。 如果這是故意的相依性，請隱藏警告或關閉此規則。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果這不是所指定 service pack 的刻意相依性，請勿隱藏此規則的警告。 在此情況下，您的應用程式可能無法在未安裝此 service pack 的系統上執行。 如果這是刻意的相依性，請抑制警告或關閉此規則。

## <a name="example"></a>範例
 下列範例顯示的類別會使用僅適用于 .NET 2.0 Service Pack 1 的 DateTimeOffset 型別。 此範例需要在專案屬性的 [目標 Framework] 下拉式清單中選取 .NET Framework 2.0。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>範例
 下列範例會以 DateTime 類型取代 DateTimeOffset 類型的使用方式，以修正先前所述的違規。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>另請參閱
 [以特定 .NET Framework 版本為目標的](../ide/targeting-a-specific-dotnet-framework-version.md)可[移植性警告](../code-quality/portability-warnings.md)
