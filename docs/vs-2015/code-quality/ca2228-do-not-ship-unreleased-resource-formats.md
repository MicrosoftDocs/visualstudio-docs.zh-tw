---
title: CA2228：不寄送未發行資源格式 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540578"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228:不要使用尚未發行版本所支援的格式建置資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源檔是使用目前不支援的版本所建立 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="rule-description"></a>規則描述
 使用的發行前版本所建立的資源檔， [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 可能無法由支援的 .NET Framework 版本使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用支援的 k 版本來建立資源 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
