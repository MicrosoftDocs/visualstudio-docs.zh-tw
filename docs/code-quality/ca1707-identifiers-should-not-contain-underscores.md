---
title: CA1707:識別項名稱不應該包含底線
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adfa0ccd63d0433d367b0e7278693608bb83d685
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234275"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707:識別項名稱不應該包含底線

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|分類|Microsoft.Naming|
|重大變更|中斷-在元件上引發時<br /><br /> 不中斷-在類型參數上引發時|

## <a name="cause"></a>原因

識別碼的名稱包含底線（\_）字元。

## <a name="rule-description"></a>規則描述

依照慣例，識別碼名稱不包含底線（\_）字元。 此規則會檢查命名空間、類型、成員和參數。

命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規

移除名稱中的所有底線字元。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則

- [CA1709識別碼的大小寫應該正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708識別碼應該不同于大小寫](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
