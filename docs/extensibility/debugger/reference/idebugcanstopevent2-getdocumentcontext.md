---
title: IDebugCanStopEvent2::GetDocumentContext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c3d409b0fa4438331d1a798e5fd6e21b2c10ca9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349549"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
取得描述這個事件的位置的文件內容。

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
[out]傳回[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面，表示目前的程式碼位置的來源檔案的文件，對應中的位置。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 一般而言，文件內容可以視為的原始程式檔中的位置。

 若要取得程式碼內容，也就是導向的程式碼的指示，呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)