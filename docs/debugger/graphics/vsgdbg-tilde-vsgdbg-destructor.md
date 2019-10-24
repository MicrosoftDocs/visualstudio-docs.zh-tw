---
title: VsgDbg：： ~ VsgDbg （析構函式） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734789"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (解構函式)
終結 `VsgDbg` 類別的實例。 如果目前正在錄製圖形資訊，則圖形記錄檔會完成並關閉，而在主動捕捉圖形資訊時使用的資源則會釋出。

## <a name="syntax"></a>語法

```C++
~VsgDbg();
```

## <a name="see-also"></a>請參閱
- [VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)