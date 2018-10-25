---
title: CA1722：識別項不應使用不正確的前置字元
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ff21b8f3c12cfa9fb3dc3ef03ca2ba2040f3769
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857603"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722：識別項不應使用不正確的前置字元

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別項具有不正確的前置詞。

## <a name="rule-description"></a>規則描述
 根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。

 型別名稱沒有特定的前置詞，而且不前面應該要有 'C'。 此規則會回報的型別名稱，例如 'CMyClass' 違規，並不會報告的類型名稱，例如 '快取' 違規。

 命名慣例提供了通用程式庫 common language runtime 為目標。 這種一致性可降低學習曲線，具有所需的新軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 識別項中移除前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1715：識別項名稱應該使用正確的前置字元](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)