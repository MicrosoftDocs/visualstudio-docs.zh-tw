---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fb78b4cbdfa2130731e3847b1a3325ab4cb3eac
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464720"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
抓取暫存器的值。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `index`

在[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉中的值，指定要從哪個暫存器取得值。

 `pRetVal`

脫銷傳回註冊的目前值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 雖然參數的大小 `pRetVal` ，其實作應該只儲存暫存器通常會保存的內容。 例如，8位暫存器只會保存指定值的最低8位。 這個8位值會在從這個方法傳回時，展開為64位。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)