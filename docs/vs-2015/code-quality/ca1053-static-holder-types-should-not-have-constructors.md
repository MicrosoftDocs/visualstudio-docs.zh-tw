---
title: CA1053：靜態預留位置類型不應該有任何構造函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539577"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053:靜態預留位置類型不應該包含建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。

## <a name="rule-description"></a>規則描述
 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 此外，因為類型沒有非靜態成員，所以建立實例並不會提供任何類型成員的存取權。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除預設的函式，或將它設為私用。

> [!NOTE]
> 如果類型未定義任何的任何函式，部分編譯器會自動建立公用預設的函式。 如果您的類型是這種情況，請新增私用預設的函式，以排除違規。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 存在於此函式的情況，表示該類型不是靜態類型。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。 請注意，原始程式碼中沒有預設的程式碼。 當此程式碼編譯成元件時，c # 編譯器會插入預設的函式，這將會違反此規則。 若要修正此錯誤，請宣告私用的函式。

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
