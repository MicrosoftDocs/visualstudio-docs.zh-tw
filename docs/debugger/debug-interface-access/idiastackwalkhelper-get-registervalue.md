---
description: IDiaStackWalkHelper：： get_registerValue 抓取 register 的值。
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa87529f90b20d7d9099dd76e294e406ae0c7a08
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161177"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
捕獲暫存器的值。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `index`

在 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md) 列舉中的值，指定要從中取得值的暫存器。

 `pRetVal`

擴展傳回註冊目前的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 儘管是參數的大小 `pRetVal` ，其實作應該只儲存註冊程式一般保存的內容。 例如，8位暫存器只會保存指定值的最低8位。 從這個方法傳回時，這個8位值會展開為64位。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)
