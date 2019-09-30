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
ms.openlocfilehash: 827a8ee01575d6d263c8f8ee423de72cfe939e39
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231171"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221:Finalizer 方法應該為 protected

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
公用類型會執行未指定家族（受保護）存取的完成項。

## <a name="rule-description"></a>規則描述
完成項必須使用系列存取修飾詞 (Modifier)。 此規則是由C#、Visual Basic 和 Visual C++編譯器強制執行。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請將完成項變更為可供家族存取。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在任何高階 .NET 語言中都不能違反這項規則;如果您要撰寫 Microsoft 中繼語言，可能會違反此檔案。

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