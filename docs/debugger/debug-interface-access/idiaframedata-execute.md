---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2587d10b613200b1bf850636f613abbb497e04de
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467446"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
執行堆疊回溯，並在堆疊引導框架介面中傳回結果。

## <a name="syntax"></a>語法

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>參數
 `frame`

在保存框架暫存器狀態的[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 下表顯示這個方法的可能傳回值。

|值|描述|
|-----------|-----------------|
|E_DIA_INPROLOG|在序言碼中，無法執行堆疊框架。|
|E_DIA_SYNTAX|框架程式中發生剖析錯誤。|
|E_DIA_FRAME_ACCESS|無法存取暫存器或記憶體。|
|E_DIA_VALUE|計算值時發生錯誤（例如，除數為零）。|

## <a name="remarks"></a>備註
 這個方法是在調試過程中呼叫，以便回溯堆疊。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)物件是由用戶端應用程式所執行，以接收暫存器的更新，以及提供方法所使用的方法 `execute` 。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)