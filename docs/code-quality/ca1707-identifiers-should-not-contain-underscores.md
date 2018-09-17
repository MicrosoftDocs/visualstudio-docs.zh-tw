---
title: CA1707：識別項不應包含底線
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74746897f8ce27a79f666ae1d691b235035b4626
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548591"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707：識別項不應包含底線

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|類別|Microsoft.Naming|
|中斷變更|中斷-時產生組件<br /><br /> 非中斷-時引發的類型參數|

## <a name="cause"></a>原因

識別項的名稱包含底線 (\_) 字元。

## <a name="rule-description"></a>規則描述

依照慣例，識別項名稱不包含底線 (\_) 字元。 此規則會檢查命名空間、 類型、 成員和參數。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規

從名稱中移除所有的底線字元。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則

- [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
