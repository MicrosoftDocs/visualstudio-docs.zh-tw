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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1221bac37b51d9aa55e31a07f2a301defa3af16e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857122"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
開啟用於查詢符號的會話。

## <a name="syntax"></a>語法

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>參數
ppSession

擴展傳回代表開啟會話的 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示此方法可能傳回的值。

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)物件先前尚未以符號來源進行初始化。|
|E_INVALIDARG|無效的 `ppSession` 參數。|
|E_OUTOFMEMORY|記憶體不足，無法開啟會話。|

## <a name="remarks"></a>備註
這個方法會開啟資料來源的 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 物件。

`IDiaSession` 物件會在資料來源中執行查詢。 會話會管理每一組 debug 符號的一個位址空間。 如果資料來源符號所描述的 .exe 或 .dll 檔在多個位址範圍中為使用中 (例如，因為多個進程已載入) ，所以應該使用每個位址範圍的一個會話。

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
