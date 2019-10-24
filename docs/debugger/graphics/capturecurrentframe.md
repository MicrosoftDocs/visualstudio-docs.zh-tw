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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736128"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
將目前框架的其餘部分捕捉到圖形記錄檔。

## <a name="syntax"></a>語法

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>備註
 如果目前正在進行另一個捕捉（例如 `BeginCapture` 函式所啟動的 capture），則該 capture 會完成並記錄到圖形記錄檔中，作為不同的框架。 之後，圖形診斷會立即開始捕獲目前框架的其餘部分，這也會記錄為不同的框架。 目前框架的結尾會以目前的呼叫來標示。

 若要捕捉框架，您必須準備您的應用程式來捕捉和記錄圖形資訊，也就是說，您必須先透過 `VsgDbg` 類別的實例呼叫[Init](init.md) ，然後才可以呼叫 `CaptureCurrentFrame`。

## <a name="see-also"></a>請參閱
- [Init](init.md)
- [BeginCapture](begincapture.md)