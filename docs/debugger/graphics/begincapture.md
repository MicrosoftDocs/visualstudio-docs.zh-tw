---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736148"
---
# <a name="begincapture"></a>BeginCapture
開始會以 `EndCapture` 結尾的 capture 間隔。

## <a name="syntax"></a>語法

```C++
void BeginCapture();
```

## <a name="remarks"></a>備註
 捕捉間隔通常會跨越一個框架的子集，例如，當您只想要捕獲特定一種繪製呼叫的圖形資訊時。 如果捕捉間隔跨越目前的呼叫，則會捕捉兩個圖形資訊的框架。 第一個框架會跨越呼叫 `BeginCapture` 與目前的呼叫之間的間隔;第二個框架會跨越出現的呼叫之後的第一個 Direct3D 事件與 `EndCapture` 的呼叫之間的間隔。

 若要捕捉間隔，您必須準備您的應用程式來捕捉和記錄圖形資訊，也就是說，您必須先透過 `VsgDbg` 類別的實例呼叫[Init](init.md) ，然後才可以呼叫 `BeginCapture` 或 `EndCapture`。

## <a name="see-also"></a>請參閱
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)