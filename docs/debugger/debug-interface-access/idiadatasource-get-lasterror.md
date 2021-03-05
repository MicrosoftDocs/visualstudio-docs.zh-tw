---
description: 抓取最後載入錯誤的檔案名。
title: IDiaDataSource：： get_lastError |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7edce9a2af6c849371360526d617d20738973cba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158312"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
抓取最後載入錯誤的檔案名。

## <a name="syntax"></a>語法

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回字串，其中包含與上次載入錯誤相關聯的 .pdb 檔案名。

## <a name="return-value"></a>傳回值
 傳回載入作業所造成的最後一個錯誤碼。 `E_INVALIDARG`如果參數為，則傳回 `pRetVal` `NULL` 。

## <a name="example"></a>範例

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
