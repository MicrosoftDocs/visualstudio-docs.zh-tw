---
title: IDiaDataSource：： get_lastError |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744980"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
抓取上一個載入錯誤的檔案名。

## <a name="syntax"></a>語法

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

脫銷傳回字串，其中包含與上次載入錯誤相關聯的 .pdb 檔案名。

## <a name="return-value"></a>傳回值
 傳回載入作業所造成的最後一個錯誤碼。 如果 `NULL` `pRetVal` 參數，則傳回 `E_INVALIDARG`。

## <a name="example"></a>範例

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)