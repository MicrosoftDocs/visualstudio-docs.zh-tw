---
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aa30598dcae08842c935d0d404cbb8b3303aefe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856877"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
依相對虛擬位址傳回框架 (RVA) 。

## <a name="syntax"></a>語法

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>參數
 relativeVirtualAddress

在感興趣的框架 RVA。

 框架

擴展傳回 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件，代表包含所提供位址的框架。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有框架資料符合指定的位址則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)