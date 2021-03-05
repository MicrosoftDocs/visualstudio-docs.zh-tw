---
description: 抓取編譯器特定的框架型別。
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c362f6a781d7596c438a3fc2c8d0acfc47f070a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157683"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
抓取編譯器特定的框架型別。

## <a name="syntax"></a>語法

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 [StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md) 列舉中的值，這個值表示編譯器特定的框架型別。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)
