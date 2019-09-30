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
ms.openlocfilehash: b3c6298c2186b6a73b4a7ef441b5f4c42c90ff6a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231053"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228:不要使用尚未發行版本所支援的格式建置資源

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

資源檔是使用目前不支援的 .NET 版本所建立。

## <a name="rule-description"></a>規則描述

支援的 .NET 版本可能無法使用 .NET 發行前版本所建立的資源檔。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用支援的 .NET 版本來建立資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。
