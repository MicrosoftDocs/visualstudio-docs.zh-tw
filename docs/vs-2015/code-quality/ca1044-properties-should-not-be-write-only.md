---
title: CA1044：屬性不應為僅寫入 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa2d07337ec48e41a9d8ad82602a387159192f92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668265"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044：屬性不應為唯寫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 Public 或 protected 屬性具有 set 存取子，但沒有 get 存取子。

## <a name="rule-description"></a>規則描述
 Get 存取子提供屬性的讀取權限，而 set 存取子則提供寫入存取權。 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者設定值，然後防止使用者看到此值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將 get 存取子新增至屬性。 或者，如果需要僅限寫入屬性的行為，請考慮將此屬性轉換成方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 強烈建議您不要隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，`BadClassWithWriteOnlyProperty` 是具有僅限寫入屬性的類型。 `GoodClassWithReadWriteProperty` 包含已更正的程式碼。

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
