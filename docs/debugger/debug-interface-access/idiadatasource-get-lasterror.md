---
title: 'Idiadatasource:: Get_lasterror |Microsoft Docs'
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
ms.openlocfilehash: 34954cd32b350a7c5f9c176deffd9943f8e05100
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641386"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
擷取最後一個載入錯誤的檔案名稱。

## <a name="syntax"></a>語法

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

[out]傳回包含與最後一個載入錯誤相關聯的.pdb 檔案名稱的字串。

## <a name="return-value"></a>傳回值
 傳回載入作業所造成的最後一個錯誤碼。 傳回`E_INVALIDARG`如果`pRetVal`參數是`NULL`。

## <a name="example"></a>範例

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)