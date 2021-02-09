---
title: VsgDbg：： VsgDbg () 的函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 466c64f3b055eef3629f0f4666529f1be4247f42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861331"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (建構函式)
`VsgDbg`使用或不准備圖形診斷的應用程式內元件，以根據指定的布林值參數，主動捕捉和記錄圖形資訊的類別實例。

## <a name="syntax"></a>語法

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>參數
 `bDefaultInit``true`若要指定圖形診斷的應用程式內元件要準備主動捕捉和記錄圖形資訊 `false` ，若要指定應用程式目前不應準備主動捕捉及記錄圖形資訊。

## <a name="remarks"></a>備註
 當呼叫此函式時 `bDefaultInit` ，如果將設定為 `true` ，則圖形記錄檔的檔案名取決於 `DONT_SAVE_VSGLOG_TO_TEMP` 和預處理器符號的定義方式，然後才 `VSG_DEFAULT_RUN_FILENAME` `vsgcapture.h` 會包含在您的應用程式中。

 當呼叫此函式時 `bDefaultInit` ，如果將設定為 `false` ，就可以準備圖形診斷的應用程式內元件，以便在稍後藉由呼叫函式來主動捕捉和記錄圖形資訊 `Init` 。

## <a name="see-also"></a>另請參閱
- [VsgDbg::~VsgDbg (解構函式)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)