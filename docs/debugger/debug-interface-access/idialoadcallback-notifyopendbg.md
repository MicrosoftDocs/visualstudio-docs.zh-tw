---
title: IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dae715a947db9c8b04a1acf3f8557b86589c26a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864695"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
在開啟候選的 dbg 檔案時呼叫。

## <a name="syntax"></a>語法

```C++
HRESULT NotifyOpenDBG ( 
   LPCOLESTR dbgPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>參數
 `dbgPath`

在Dbg 檔案的完整路徑。

 `resultCode`

在此程式碼表示套用至這個檔案的負載成功 (`S_OK`) 或失敗。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 通常會忽略傳回碼。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)