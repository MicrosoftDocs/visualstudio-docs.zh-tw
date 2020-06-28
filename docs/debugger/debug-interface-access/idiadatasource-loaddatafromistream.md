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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a6a19d926ead4c2c38ff69544311caa1f726b3e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468508"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
準備儲存在程式資料庫（.pdb）檔案中的 debug 資料，此檔案會透過記憶體中的資料流程來存取。

## <a name="syntax"></a>語法

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>參數
 pIStream

在<xref:IStream>物件，代表要使用的資料流程。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 下表顯示這個方法的可能傳回值。

|值|描述|
|-----------|-----------------|
|E_PDB_FORMAT|嘗試存取具有過時格式的檔案。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|資料來源已準備就緒。|

## <a name="remarks"></a>備註
 這個方法可讓您透過物件從記憶體中取得可執行檔的偵錯工具資料 <xref:IStream> 。

 若要載入不具驗證的 .pdb 檔案，請使用[IDiaDataSource：： loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。

 若要根據特定準則來驗證 .pdb 檔案，請使用[IDiaDataSource：： loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。

 若要取得資料載入進程（透過回呼機制）的存取權，請使用[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)