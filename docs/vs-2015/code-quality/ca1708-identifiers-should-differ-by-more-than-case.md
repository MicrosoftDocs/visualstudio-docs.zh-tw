---
title: CA1708：識別碼應該不同于大小寫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22a33c852b941b4c7e7398416aa1e74e69ff1786
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544036"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708:識別項名稱不應該只靠大小寫區別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 當兩種類型、成員、參數或完整命名空間的名稱轉換成小寫時，兩者的名稱都相同。

## <a name="rule-description"></a>規則描述
 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 例如， [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 是廣泛使用的不區分大小寫語言。

 此規則只會在公開可見的成員上引發。

## <a name="how-to-fix-violations"></a>如何修正違規
 當與其他識別碼比較不區分大小寫時，請選取唯一的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 程式庫可能無法在中的所有可用語言中使用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="example-of-a-violation"></a>違規範例
 下列範例示範此規則的違規。

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
