---
description: 從可執行檔中的指定位移開始讀取指定的位元組數目。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9986ba6d493353644d8387b2df36a96cbf542933
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157360"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
從可執行檔中的指定位移開始讀取指定的位元組數目。

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

在要讀取的位元組數目。

 pcbData

擴展傳回讀取的位元組數目。

 data[]

[in，out]以讀取自檔案的位元組填入的陣列。

## <a name="remarks"></a>備註
 DIA 支援程式碼會呼叫這個方法，以使用絕對檔案位移從可執行檔載入資料位元組。 呼叫這個方法的方式是支援 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
