---
title: VsgDbg：： VsgDbg （函式） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734752"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (建構函式)
根據指定的布林參數，使用或不准備圖形診斷的應用程式內元件，以主動捕捉並記錄圖形資訊，以建立 `VsgDbg` 類別的實例。

## <a name="syntax"></a>語法

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>參數
 `bDefaultInit` `true` 指定要準備圖形診斷的應用程式內元件，以主動捕捉並記錄圖形資訊; `false`，指定應用程式目前不應準備好主動捕捉和記錄圖形資訊。

## <a name="remarks"></a>備註
 當使用 `bDefaultInit` 設定為 `true` 來呼叫此函式時，圖形記錄檔的檔案名取決於應用程式中包含 `vsgcapture.h` 之前，`DONT_SAVE_VSGLOG_TO_TEMP` 和 `VSG_DEFAULT_RUN_FILENAME` 預處理器符號的定義方式。

 當使用 `bDefaultInit` 設定為 `false` 來呼叫此函式時，圖形診斷的應用程式內元件可以藉由呼叫 `Init` 函數來準備，以便在稍後主動捕捉並記錄圖形資訊。

## <a name="see-also"></a>請參閱
- [VsgDbg::~VsgDbg (解構函式)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)