---
description: IDiaStackWalkHelper：:p ut_registerValue 設定註冊的值。
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdc66faea9537759e9754ce799339175db585673
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156822"
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

在 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md) 列舉中的值，指定要寫入的暫存器。

 `NewVal`

在新的暫存器值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 儘管值的大小，其實作應該只儲存註冊程式一般保存的內容。 例如，8位的暫存器只會保留指定值的最低8位。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)
