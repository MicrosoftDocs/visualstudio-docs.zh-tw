---
description: 從可執行檔 (RVA) 中，讀取指定的相對虛擬位址開始的指定位元組數目。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4c3d51ce1d2a54583df41fb4c6dd17dcfd679ad1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157326"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
從可執行檔 (RVA) 中，讀取指定的相對虛擬位址開始的指定位元組數目。

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

在要開始讀取之可執行檔中的 RVA。

 `cbData`

在要讀取的位元組數目。

 `pcbData`

擴展傳回讀取的位元組數目。

 `data[]`

[in，out]以讀取自檔案的位元組填入的陣列。

## <a name="remarks"></a>備註
 DIA 支援程式碼會呼叫這個方法，以使用相對虛擬位址從可執行檔載入資料位元組。 呼叫這個方法的方式是支援 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
