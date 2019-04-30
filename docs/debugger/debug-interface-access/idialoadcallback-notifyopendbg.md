---
title: IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97ca8b06a480d2fddb2002a0b9a19f878caa58f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828615"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
在開啟候選.dbg 檔案時呼叫。

## <a name="syntax"></a>語法

```C++
HRESULT NotifyOpenDBG ( 
   LPCOLESTR dbgPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>參數
 `dbgPath`

[in].Dbg 檔案完整路徑。

 `resultCode`

[in]表示成功的程式碼 (`S_OK`) 或失敗的負載套用至這個檔案。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回碼通常會被忽略。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)