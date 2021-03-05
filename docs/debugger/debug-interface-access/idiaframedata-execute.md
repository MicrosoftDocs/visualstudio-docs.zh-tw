---
description: 執行堆疊回溯，並且在堆疊引導框架介面中傳回結果。
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 483854d0bea61af1bf8bd1f5338770fcc49b37be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157809"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
執行堆疊回溯，並且在堆疊引導框架介面中傳回結果。

## <a name="syntax"></a>語法

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>參數
 `frame`

在保存框架暫存器狀態的 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示此方法可能傳回的值。

|值|描述|
|-----------|-----------------|
|E_DIA_INPROLOG|在序言程式碼中，無法執行堆疊框架。|
|E_DIA_SYNTAX|在框架程式中發生剖析錯誤。|
|E_DIA_FRAME_ACCESS|無法存取暫存器或記憶體。|
|E_DIA_VALUE|計算值時發生錯誤 (例如，零除) 。|

## <a name="remarks"></a>備註
 在偵錯工具期間會呼叫這個方法，以回溯堆疊。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)物件是由用戶端應用程式所執行，以接收暫存器的更新，並提供方法所使用的方法 `execute` 。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
