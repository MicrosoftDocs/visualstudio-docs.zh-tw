---
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea924ffd92b6e099302c1bb8e2857dab47479
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855757"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
抓取運算式或語句結尾的以一為基礎的來源資料行編號。

## <a name="syntax"></a>語法

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回運算式或語句結束的資料行編號。 如果值為零，則不會顯示資料行結尾資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的資料行值，是行上語句最後一個字元後面的位置的位元組位移。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)