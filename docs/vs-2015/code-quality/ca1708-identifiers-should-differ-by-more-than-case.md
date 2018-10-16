---
title: CA1708： 識別項不應該不同不僅為大小寫 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07f4b9f9a69de3458bf0f7ea7dcb316e2e9a086a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187638"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708：識別項名稱不應該只靠大小寫區別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 轉換成小寫字母時，兩個型別、 成員、 參數或完整限定的命名空間的名稱完全相同。

## <a name="rule-description"></a>規則描述
 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 比方說，[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]是廣泛使用不區分大小寫的語言。

 上公開可見的成員，就會引發此規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取 是唯一的它是以不區分大小寫的方式相較於其他識別項的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 程式庫可能無法使用所有可用的語言中[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。

## <a name="example-of-a-violation"></a>發生違規的範例
 下列範例會示範這項規則的違規情形。

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



