---
title: CA2228：不要出貨建置資源格式 |Microsoft Docs
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
ms.openlocfilehash: 9297ea0bb24eed54d0134a5f3c0fce87e6757adb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662879"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228：不要使用尚未發行版本所支援的格式建置資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源檔是使用目前不支援的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本所建立。

## <a name="rule-description"></a>規則描述
 支援的 .NET Framework 版本可能無法使用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 發行前版本所建立的資源檔。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用支援的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k 版本來建立資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
