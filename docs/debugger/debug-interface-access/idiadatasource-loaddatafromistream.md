---
title: IDiaDataSource：： loadDataFromIStream |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adf9d25f2ba6afac0510c95790dc8608b22243c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857136"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
準備程式資料庫中儲存的 debug 資料 ( .pdb) 透過記憶體中資料流程存取的檔案。

## <a name="syntax"></a>語法

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>參數
 pIStream

在 <xref:IStream> 物件，表示要使用的資料流程。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示此方法可能傳回的值。

|值|描述|
|-----------|-----------------|
|E_PDB_FORMAT|嘗試存取已淘汰格式的檔案。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|已經備妥資料來源。|

## <a name="remarks"></a>備註
 這個方法可讓您透過物件從記憶體取得可執行檔的偵錯工具資料 <xref:IStream> 。

 若要載入不含驗證的 .pdb 檔，請使用 [IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 方法。

 若要根據特定準則驗證 .pdb 檔案，請使用 [IDiaDataSource：： loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 方法。

 若要透過) 的回呼機制取得資料載入進程 (的存取權，請使用 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)