---
title: "CA1053： 靜態預留位置類型不應該有建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9e9d6272fbb21644daab96bb3ccd7d02b023840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053：靜態預留位置類型不應包含建構函式
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。  
  
## <a name="rule-description"></a>規則描述  
 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 此外，因為類型沒有非靜態成員，建立執行個體不提供存取任何類型的成員。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除預設建構函式或私用。  
  
> [!NOTE]
>  如果類型未定義任何建構函式，某些編譯器自動建立的公用預設建構函式。 如果這是您的型別使用的情況下，加入私用的預設建構函式，以消除違規。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 建構函式的存在會建議的類型不是靜態類型。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型。 請注意，沒有預設建構函式的原始程式碼中。 當此程式碼編譯成組件時，C# 編譯器會插入會違反此規則的預設建構函式。 若要修正此問題，宣告私用建構函式。  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]