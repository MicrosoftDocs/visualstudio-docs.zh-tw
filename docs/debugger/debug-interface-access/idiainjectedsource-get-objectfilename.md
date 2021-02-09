---
title: IDiaInjectedSource::get_objectFilename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_objectFilename method
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a539d0fe6f99650254a53db9b8dd38c98fecae9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855785"
---
# <a name="idiainjectedsourceget_objectfilename"></a>IDiaInjectedSource::get_objectFilename
抓取來源編譯的目標目的檔名。

## <a name="syntax"></a>語法

```C++
HRESULT get_objectFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回編譯來源的目標目的檔名。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)