---
title: EndCapture | Microsoft Docs
description: 使用 VsgDbg 類別的 EndCapture 方法，以結束以 BeginCapture 啟動的捕捉間隔。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727827"
---
# <a name="endcapture"></a>EndCapture
結束以啟動的捕獲間隔 `BeginCapture` 。

## <a name="syntax"></a>語法

```C++
void EndCapture();
```

## <a name="remarks"></a>備註
 捕捉間隔通常會跨越一個框架的子集，例如，當您只想要捕獲特定種類之繪製呼叫的圖形資訊時。 如果捕捉間隔超過呼叫的範圍，則會捕捉兩個圖形資訊框架。 第一個框架橫跨呼叫和目前的呼叫之間的間隔 `BeginCapture` ; 第二個框架則是在呼叫出現的和呼叫之後，跨越第一個 Direct3D 事件之間的間隔 `EndCapture` 。

 若要取得間隔，您必須準備您的應用程式來捕獲和記錄圖形資訊，也就是說，您必須先透過類別的實例呼叫 [Init](init.md) ， `VsgDbg` 才能呼叫 `BeginCapture` 或 `EndCapture` 。

## <a name="see-also"></a>請參閱
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)