---
title: IDiaInjectedSource::get_virtualFilename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78bb087f7e5b66d68e24d66315d9edcd15b06544
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864870"
---
# <a name="idiainjectedsourceget_virtualfilename"></a>IDiaInjectedSource::get_virtualFilename
抓取提供給非檔案原始碼的名稱;也就是插入的程式碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_virtualFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回為插入的非檔案原始程式碼提供的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)