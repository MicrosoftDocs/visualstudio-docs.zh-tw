---
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 48bffc8e07ede412c9d33176fdaf29ba85ba1f0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856870"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
依虛擬位址 (VA) 傳回框架。

## <a name="syntax"></a>語法

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>參數
 virtualAddress

在感興趣的框架 VA。

 框架

擴展傳回 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件，這個物件表示包含所提供位址的框架。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有框架資料符合指定的位址則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)