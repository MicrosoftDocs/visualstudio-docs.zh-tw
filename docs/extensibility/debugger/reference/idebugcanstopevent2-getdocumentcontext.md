---
title: IDebugCanStopevent2::獲取文檔上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3dc5e4bd7144db7fa94425371488bfd8c0e57ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734549"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
獲取描述此事件位置的文檔上下文。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>參數
`ppDocCxt`\
[出]返回[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面,該介面表示與目前代碼位置對應的源文件文檔中的位置。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 通常,文檔上下文可以被視為源檔中的位置。

 要取得針對程式碼指令的程式碼上下文,請呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
