---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0c0052ca7183a0c53080a4e51bddd2cdfbf72ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854889"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
這個方法會將指定的區域變數值視為原始位元組。

## <a name="syntax"></a>語法

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>參數
 `pInstance`

在 `IDiaLVarInstance` 物件，代表要取得其值的本機變數實例。

 `cbDataMax`

在所指向之緩衝區中的最大位元組數目 `pbData` 。  () 最多可有8個位元組 `sizeof(ULONGLONG)` 。

 `pcbData`

擴展傳回儲存在緩衝區中的實際位元組數目。

 `pbData`

擴展要填入資料的緩衝區。 不可為 `NULL`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)