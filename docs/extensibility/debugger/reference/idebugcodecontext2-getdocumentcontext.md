---
description: 取得對應于這個程式碼內容的檔內容。
title: IDebugCodeCoNtext2：： GetDocumentCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80420f12369ef038c2faccb51c9b1bfc9b0073a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088415"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
取得對應于這個程式碼內容的檔內容。 檔內容代表原始程式檔中，對應至產生此指令之原始程式碼的位置。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>參數
`ppSrcCxt`\
擴展傳回對應至程式碼內容的 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 物件。 如果 `S_OK` 傳回，則此應為非 `null` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 當參數為時，例如當 `E_FAIL` `out` 程式 `null` 代碼內容沒有相關聯的來源位置時，debug engine 應該會傳回失敗碼。

## <a name="remarks"></a>備註
 一般而言，檔內容可視為原始程式檔中的位置，而程式碼內容是程式碼指令在執行資料流程中的位置。

## <a name="see-also"></a>另請參閱
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
