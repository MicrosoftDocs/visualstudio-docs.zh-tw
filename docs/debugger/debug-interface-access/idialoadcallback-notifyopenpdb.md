---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbcf8aff8dc18776cbcb09a5fa3f13edca4cd7a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743058"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
當候選的 .pdb 檔案開啟時呼叫。

## <a name="syntax"></a>語法

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>參數
 `pdbPath`

在.Pdb 檔案的完整路徑。

 `resultCode`

在表示套用至這個檔案的成功（`S_OK`）或負載失敗的程式碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。 傳回碼通常會被忽略。

## <a name="see-also"></a>請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)