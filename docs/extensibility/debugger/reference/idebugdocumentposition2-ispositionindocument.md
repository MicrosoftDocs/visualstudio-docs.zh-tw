---
description: 判斷檔位置是否包含在指定的檔中。
title: IDebugDocumentPosition2：： IsPositionInDocument |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4800f3735e2d015e3638a642e8c0d54829ddd4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154284"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
判斷檔位置是否包含在指定的檔中。

## <a name="syntax"></a>語法

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>參數
`pDoc`\
在代表包含檔候選項的 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法主要用於設定 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 介面中的中斷點。 載入檔時，會呼叫中斷點位置，以判斷檔是否包含這個位置。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
