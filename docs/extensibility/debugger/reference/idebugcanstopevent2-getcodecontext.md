---
title: IDebugCanStopEvent2：： GetCodeCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94c129d7d50bc747291d8a178d73c06655e65414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734571"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
取得描述這個事件位置的程式碼內容。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>參數
`ppCodeContext`\
擴展傳回代表目前程式碼位置的 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 在大部分的執行時間架構中，可以將程式碼內容視為程式執行資料流程中的位址，指向特定的指令。

 若要取得檔內容（面向于原始程式碼的行），請呼叫 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
