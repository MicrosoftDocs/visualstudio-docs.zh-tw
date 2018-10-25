---
title: CA1708：識別項名稱不應該只靠大小寫區別
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2bda5a9f5d569057455af9e31fb5d6852c9881e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815490"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708：識別項名稱不應該只靠大小寫區別

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 轉換成小寫字母時，兩個型別、 成員、 參數或完整限定的命名空間的名稱完全相同。

## <a name="rule-description"></a>規則描述
 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 比方說，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]是廣泛使用不區分大小寫的語言。

 上公開可見的成員，就會引發此規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取 是唯一的它是以不區分大小寫的方式相較於其他識別項的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 程式庫可能無法使用.NET Framework 中的所有可用語言。

## <a name="example-of-a-violation"></a>發生違規的範例
 下列範例會示範這項規則的違規情形。

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)