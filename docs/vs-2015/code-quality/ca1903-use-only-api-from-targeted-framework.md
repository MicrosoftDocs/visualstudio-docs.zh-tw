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
ms.openlocfilehash: 7dec130e4a4704bea347f94ff57d354a4465ddd6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604970"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903：只使用來自目標架構的 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[CA1903：僅使用來自目標架構的 API](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework)。

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Category|Microsoft 可攜性|
|中斷變更|中斷-針對外部可見成員或類型的簽章引發。<br /><br /> 非中斷-在方法的主體中引發時。|

## <a name="cause"></a>原因
 成員或類型使用的成員或類型，不是在專案的目標架構所包含的 Service Pack 中。

## <a name="rule-description"></a>規則描述
 新成員和類型包含在 .NET Framework 2.0 Service Pack 1 和2，.NET Framework 3.0 Service Pack 1 和2，以及 .NET Framework 3.5 Service Pack 1。 以 .NET Framework 的主要版本為目標的專案，可能會不小心地對這些新的 Api 採取相依性。 為避免此相依性，此規則會在任何新成員和類型的使用方式下引發，而此專案的目標架構預設並不包含該物件。

 **目標 Framework 和 Service Pack 相依性**

|||
|-|-|
|當目標 framework 為|在中引進的成員使用方式時引發|
|.NET Framework 2.0|.NET Framework 2.0 SP1，.NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 若要變更專案的目標 framework，請參閱以[特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要移除 Service Pack 的相依性，請移除新成員或類型的所有使用方式。 如果這是有意的相依性，請隱藏警告或關閉此規則。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果這不是刻意依賴指定的 Service Pack，請勿隱藏此規則的警告。 在此情況下，您的應用程式可能無法在未安裝此 Service Pack 的系統上執行。 如果這是刻意的相依性，請隱藏警告或關閉此規則。

## <a name="example"></a>範例
 下列範例顯示的類別會使用僅適用于 .NET 2.0 Service Pack 1 的 DateTimeOffset 類型。 這個範例需要在專案屬性的 [目標 Framework] 下拉式清單中選取 .NET Framework 2.0。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>範例
 下列範例會以 DateTime 類型取代 DateTimeOffset 類型的用法，藉以修正先前描述的違規。

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>請參閱
 [以特定 .NET Framework 版本為目標的](../ide/targeting-a-specific-dotnet-framework-version.md)可[移植性警告](../code-quality/portability-warnings.md)
