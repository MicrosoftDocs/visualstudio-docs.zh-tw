---
title: CA2228:不要使用尚未發行版本所支援的格式建置資源
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4355db8b15a3869e785589170bec3f80e8f08fbb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923404"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228:不要使用尚未發行版本所支援的格式建置資源

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 資源檔案是使用目前不支援的.NET framework 版本所建置的。

## <a name="rule-description"></a>規則描述
 使用發行前版本的.NET framework 所建置的資源檔可能不支援的.NET framework 的版本。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，建置使用支援的.NET Framework 版本的資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
