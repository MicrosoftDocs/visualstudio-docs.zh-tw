---
title: CA1903:使用來自目標架構的 API |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647151"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903:只使用來自目標架構的 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[CA1903:只使用來自目標架構 API](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework)。  
  
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
  
 若要變更專案的目標架構，請參閱[特定的.NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要移除的相依性的 service pack，請移除新的成員或類型的所有使用方式。 如果這是刻意的相依性時，隱藏警告，或關閉這項規則。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果這不是刻意的相依性，於指定的服務組件，則請勿隱藏此規則的警告。 在此情況下，您的應用程式可能無法在系統上執行未安裝此 service pack。 隱藏警告，或關閉這項規則，如果這是刻意的相依性。  
  
## <a name="example"></a>範例  
 下列範例顯示使用的型別 DateTimeOffset，僅供以.NET 2.0 Service Pack 1 的類別。 這個範例需要在目標 Framework 下拉式清單中，在專案屬性中已選取 .NET Framework 2.0。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>範例  
 下列範例會將先前所述的違規修正 DateTimeOffset 類型的使用方式取代成日期時間型別。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [可攜性警告](../code-quality/portability-warnings.md)   
 [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)
