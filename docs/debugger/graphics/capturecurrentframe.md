---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736128"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
將目前框架的其餘部分捕獲到圖形記錄檔。

## <a name="syntax"></a>語法

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>備註
 如果另一個捕捉正在進行中（例如，由函式啟動的 capture `BeginCapture` ），該 capture 就會完成，並記錄到圖形記錄檔中，做為不同的框架。 之後，圖形診斷會開始捕獲目前框架的其餘部分，也會記錄為不同的畫面格。 目前框架的結尾會以目前的呼叫來標示。

 若要取得畫面格，您必須準備您的應用程式來捕獲和記錄圖形資訊，也就是說，您必須先透過類別的實例呼叫 [Init](init.md) ， `VsgDbg` 才能呼叫 `CaptureCurrentFrame` 。

## <a name="see-also"></a>另請參閱
- [Init](init.md)
- [BeginCapture](begincapture.md)