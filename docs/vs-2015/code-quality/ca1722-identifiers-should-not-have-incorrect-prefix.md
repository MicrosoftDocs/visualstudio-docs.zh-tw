---
title: CA1722：識別碼不應有不正確的前置詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a7f4f932f8e2db9a558d7440d8965ce5924043b8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544478"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722:識別項名稱不應該使用不正確的前置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼有不正確的前置詞。

## <a name="rule-description"></a>規則描述
 根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。

 型別名稱沒有特定的前置詞，且前面不能加上 ' C '。 此規則會報告型別名稱（例如 ' CMyClass '）的違規，而且不會報告型別名稱違規，例如 ' Cache '。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 請移除識別碼中的前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1715:識別項名稱應該使用正確的前置字元](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
