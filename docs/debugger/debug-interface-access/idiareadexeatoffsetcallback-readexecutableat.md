---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 741fd417fa6ce8e8a2faf714038aaa3d0f798233
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466473"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
從可執行檔的指定位移開始，讀取指定的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>參數
 fileOffset

在可執行檔中要開始讀取的位移。

 cbData

在要讀取的位元組數。

 pcbData

脫銷傳回讀取的位元組數目。

 data[]

[in、out]填入的陣列，其中包含從檔案讀取的位元組。

## <a name="remarks"></a>備註
 DIA 支援程式碼會呼叫這個方法，以使用絕對檔案位移從可執行檔載入資料位元組。 這個方法是在支援[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法時呼叫。

## <a name="see-also"></a>另請參閱
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)