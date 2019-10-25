---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619ed78584a9fe897b19d6ac2ffd4c28838c61ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741375"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
設定註冊的值。

## <a name="syntax"></a>語法

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>參數
 `index`

在[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉中的值，指定要寫入的暫存器。

 `NewVal`

在新的暫存器值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 雖然值的大小，但執行應該只會儲存暫存器通常會保存的內容。 例如，8位暫存器只會保留指定值的最低8位。

## <a name="see-also"></a>請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)