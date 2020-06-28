---
title: IDiaDataSource：： openSession |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b49c90374975865edcac8a94c504e1fa991d711a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468501"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
開啟查詢符號的會話。

## <a name="syntax"></a>語法

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>參數
ppSession

脫銷傳回代表開啟會話的[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件。

## <a name="return-value"></a>傳回值
如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 下表顯示這個方法的可能傳回值。

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)物件先前尚未使用符號來源進行初始化。|
|E_INVALIDARG|無效的 `ppSession` 參數。|
|E_OUTOFMEMORY|記憶體不足，無法開啟會話。|

## <a name="remarks"></a>備註
這個方法會開啟資料來源的[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件。

`IDiaSession`物件會在資料來源中執行查詢。 會話會管理每一組 debug 符號的一個位址空間。 如果資料來源符號所描述的 .exe 或 .dll 檔案在多個位址範圍中為使用中（例如，因為多個進程已載入），則應該使用每個位址範圍的一個會話。

## <a name="example"></a>範例

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>另請參閱
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
