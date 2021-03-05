---
description: 以數種形式的其中一種取得檔的名稱。
title: IDebugDocument2：： GetName |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b68fb60cb13d88941b21f6625e6cc0e38ceeda4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166537"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
以數種形式的其中一種取得檔的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>參數
`gnType`\
在 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 列舉中的值，可決定要傳回的名稱類型。

`pbstrFileName`\
擴展傳回包含檔案名稱的字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 例如，這個方法可以將檔的名稱以標題或檔案名或檔案名的一部分傳回。

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
