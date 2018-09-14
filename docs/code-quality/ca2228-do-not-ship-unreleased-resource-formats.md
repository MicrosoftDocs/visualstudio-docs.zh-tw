---
title: CA2228：不要使用尚未發行版本所支援的格式建置資源
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2823933e4792dd6127ffbd4b1bfe5dfe1b71a0c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547541"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228：不要使用尚未發行版本所支援的格式建置資源
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源檔是使用新版[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，目前不支援。

## <a name="rule-description"></a>規則描述
 使用發行前版本所建置的資源檔[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可能不支援的.NET framework 的版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，建置使用支援的版本之資源[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。