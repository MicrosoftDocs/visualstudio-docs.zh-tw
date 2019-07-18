---
title: CA2223:成員不應該由多個傳回的型別不同 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6a460cd01d671d347e1cd126d009fe19e140cc69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201598"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223:成員不應該只有在傳回類型上不同
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
 兩個公用或受保護的成員具有除了傳回型別之外完全相同的簽章。

## <a name="rule-description"></a>規則描述
 雖然通用語言執行平台允許使用傳回的型別區分其他完全相同的成員，這項功能不在 Common Language Specification，也不是.NET 程式設計語言的常見功能。 當成員只有不同傳回型別時，開發人員和開發工具可能不正確區別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更成員的設計，讓它們都是唯一只根據其名稱與參數類型，或不公開的成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例中，在 Microsoft intermediate language (MSIL)，顯示違反此規則的型別。 請注意，不能使用 C# 或 Visual Basic.NET 違反此規則。

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary
```
