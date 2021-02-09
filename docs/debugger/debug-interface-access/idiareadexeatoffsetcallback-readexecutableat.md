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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d70ca331d56fd423e7bfbfc4596b8f3ef5954b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855512"
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