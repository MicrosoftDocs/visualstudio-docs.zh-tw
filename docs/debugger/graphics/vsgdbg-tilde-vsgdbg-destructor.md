---
title: VsgDbg：： ~ VsgDbg () 的函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734789"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (解構函式)
終結類別的實例 `VsgDbg` 。 如果正在記錄圖形資訊，圖形記錄檔將會完成並關閉，而在主動捕獲圖形資訊時使用的資源則會放開。

## <a name="syntax"></a>語法

```C++
~VsgDbg();
```

## <a name="see-also"></a>另請參閱
- [VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)