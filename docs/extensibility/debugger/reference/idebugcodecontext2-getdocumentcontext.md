---
title: IDebugCode上下文2::獲取文檔上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734340"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
獲取對應於此代碼上下文的文檔上下文。 文檔上下文表示源文件中對應於生成此指令的原始程式碼的位置。

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
[出]返回與代碼上下文對應的[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件。 如果`S_OK`傳回,則 th`null`應是非 。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 除錯引擎應傳回故障程式`E_FAIL``out`碼,`null`例如參數為 參數時,例如程式碼上下文沒有關聯的來源位置。

## <a name="remarks"></a>備註
 通常,文檔上下文可以被視為源檔中的位置,而代碼上下文是執行流中代碼指令的位置。

## <a name="see-also"></a>另請參閱
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
