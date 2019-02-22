---
title: CA2221:Finalizer 方法應該為 protected
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3da7f0da3901511e0f14e48b3ff0500928e3774
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917476"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221:Finalizer 方法應該為 protected

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型會實作完成項，不會指定系列 （受保護） 的存取。

## <a name="rule-description"></a>規則描述
 完成項必須使用系列存取修飾詞 (Modifier)。 此規則會強制執行 C#、 Visual Basic 和 Visual c + + 編譯器。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更系列存取完成項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 無法以任何高層級的.NET 語言; 違反此規則如果您正在撰寫 Microsoft Intermediate Language，它可以是違反了。

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>另請參閱

- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)