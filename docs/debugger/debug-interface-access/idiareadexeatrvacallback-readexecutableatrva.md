---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a417669c381036fffac87b4d7e56c66fa31f728
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466459"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
從可執行檔讀取指定的位元組數目，從指定的相對虛擬位址（RVA）開始。

## <a name="syntax"></a>語法

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>參數
 `relativeVirtualAddress`

在要開始讀取的可執行檔中的 RVA。

 `cbData`

在要讀取的位元組數。

 `pcbData`

脫銷傳回讀取的位元組數目。

 `data[]`

[in、out]填入的陣列，其中包含從檔案讀取的位元組。

## <a name="remarks"></a>備註
 DIA 支援程式碼會呼叫這個方法，以使用相對虛擬位址從可執行檔載入資料位元組。 這個方法是在支援[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法時呼叫。

## <a name="see-also"></a>另請參閱
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)