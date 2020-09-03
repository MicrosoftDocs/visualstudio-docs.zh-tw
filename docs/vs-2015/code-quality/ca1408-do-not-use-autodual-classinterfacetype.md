---
title: CA1408：請勿使用 AutoDual Classinterfacetype.none |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534871"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408:不要使用 AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見類型會標示 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 設定為值的屬性 `AutoDual` <xref:System.Runtime.InteropServices.ClassInterfaceType> 。

## <a name="rule-description"></a>規則描述
 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 依預設，如果 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 未指定屬性，則會使用僅分派介面。

 除非以其他方式標示，否則 COM 會看到所有的公用非泛型型別;COM 看不到所有非公用和泛型型別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性的值變更 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 為的 `None` 值， <xref:System.Runtime.InteropServices.ClassInterfaceType> 並明確地定義介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非確定類型及其基底類型的版面配置不會在未來版本中變更，否則請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類別，以及將類別重新宣告為使用明確介面的類別。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1403:自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412:ComSource 介面必須標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>另請參閱
 [簡介類別介面](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[合格的 .net](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [型別與非受控碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)交互操作的互通性
