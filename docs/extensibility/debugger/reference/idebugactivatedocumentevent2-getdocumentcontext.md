---
title: IDebugActivateDocumentEvent2：： GetDocumentCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1b68c10c290dcf685e1eaa5fef907e27be7452f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736636"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
取得檔內容，描述檔中要由 debug 封裝啟用的位置。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>參數
`ppDocContext`\
擴展傳回代表原始程式檔檔中之位置的 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 物件。

## <a name="remarks"></a>備註
 例如，此位置可能會用來顯示插入號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
