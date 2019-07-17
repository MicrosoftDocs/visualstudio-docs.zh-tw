---
title: CA2228:不要使用尚未發行的格式建置的資源 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2e49953a95da10653cd29132e003fa36de5b8d4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142430"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228:不要使用尚未發行版本所支援的格式建置資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源檔是使用新版[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，目前不支援。

## <a name="rule-description"></a>規則描述
 使用發行前版本所建置的資源檔[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]可能不支援的.NET framework 的版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，建置使用支援的版本之資源[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
