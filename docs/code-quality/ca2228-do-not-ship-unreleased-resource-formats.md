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
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714974"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228:不要使用尚未發行版本所支援的格式建置資源

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

使用目前不支援的.NET 版本的建置資源檔。

## <a name="rule-description"></a>規則描述

使用.NET 的發行前版本所建置的資源檔可能會無法使用所支援的.NET 版本。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，建置使用支援的.NET 版本的資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。
