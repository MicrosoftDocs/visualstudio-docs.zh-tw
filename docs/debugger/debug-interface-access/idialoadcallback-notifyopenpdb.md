---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 468aef9faf4aa6c7c1b7ddebb1fd0c15445d61a2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466739"
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

在指出套用至此檔案的成功（ `S_OK` ）或負載失敗的程式碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 傳回碼通常會被忽略。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)