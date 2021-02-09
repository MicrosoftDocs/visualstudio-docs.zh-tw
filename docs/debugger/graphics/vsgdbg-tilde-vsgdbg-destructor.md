---
title: VsgDbg：： ~ VsgDbg () 的函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861344"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (解構函式)
終結類別的實例 `VsgDbg` 。 如果正在記錄圖形資訊，圖形記錄檔將會完成並關閉，而在主動捕獲圖形資訊時使用的資源則會放開。

## <a name="syntax"></a>語法

```C++
~VsgDbg();
```

## <a name="see-also"></a>另請參閱
- [VsgDbg::VsgDbg (建構函式)](vsgdbg-vsgdbg-constructor.md)