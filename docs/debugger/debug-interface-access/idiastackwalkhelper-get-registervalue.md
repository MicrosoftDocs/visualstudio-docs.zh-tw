---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275941aaf3a1eb2cab6554b18c6d9aa66605121a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831828"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
擷取暫存器的值。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `index`

[in]值，以從[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉指定的註冊並取得的值。

 `pRetVal`

[out]傳回目前的暫存器值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 大小雖然`pRetVal`參數，實作應儲存只哪些暫存器通常會保留。 比方說，8 位元暫存器保留只最低 8 位元的指定值。 這個 8 位元值已擴充成 64 位元，從這個方法傳回時。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)