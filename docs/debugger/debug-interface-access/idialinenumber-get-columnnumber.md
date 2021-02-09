---
title: IDiaLineNumber::get_columnNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ec9075be8ab003cda087b37c13a0f2ef9c481dff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864800"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
抓取運算式或語句開始的資料行編號。

## <a name="syntax"></a>語法

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回運算式或語句開始的資料行編號。 如果值為零，則不會顯示資料行資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的資料行值，就是該行與語句的第一個字元之間的位元組位移。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)