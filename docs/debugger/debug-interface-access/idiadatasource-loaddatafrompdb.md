---
title: 'Idiadatasource:: Loaddatafrompdb |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb34098f8d69d3c8618c406eff9666d52eace1f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554140"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
隨即開啟，並準備做為偵錯資料來源的程式資料庫 (.pdb) 檔。

## <a name="syntax"></a>語法

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>參數
pdbPath

[in].pdb 檔案的路徑。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。

|值|描述|
|-----------|-----------------|
|E_PDB_NOT_FOUND|無法開啟檔案，或判斷檔案有無效的格式。|
|E_PDB_FORMAT|嘗試存取已過時的格式的檔案。|
|E_INVALIDARG|無效的參數。|
|E_UNEXPECTED|資料來源已準備好了。|

## <a name="remarks"></a>備註
這個方法會載入偵錯資料直接從.pdb 檔案。

若要驗證對特定準則的.pdb 檔，請使用[idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。

若要存取的資料載入程序 （透過回呼的機制），請使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。

若要直接從記憶體中載入的.pdb 檔案，請使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。

## <a name="example"></a>範例

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
