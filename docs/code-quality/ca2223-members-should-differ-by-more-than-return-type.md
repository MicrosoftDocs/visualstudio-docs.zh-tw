---
title: "CA2223： 成員不應該不同的多個傳回型別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 312ba498965cea7404e66d15f9136ac9a364da98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223：成員不應該只有在傳回型別上不同
|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|CheckId|CA2223|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 兩個公用或受保護的成員具有除了傳回型別之外完全相同的簽章。  
  
## <a name="rule-description"></a>規則描述  
 雖然通用語言執行平台允許使用傳回型別區分其他部分相同的成員，這項功能不在 Common Language Specification，也不是.NET 程式語言共通功能。 當成員只有不同的傳回型別時，開發人員和開發工具可能不正確區分它們。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請變更之成員的設計，以便只根據其名稱和參數類型或不公開的成員。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例中，Microsoft intermediate language (MSIL)，顯示違反此規則的類型。 請注意，不能使用 C# 或 Visual Basic.NET 違反此規則。  
  
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