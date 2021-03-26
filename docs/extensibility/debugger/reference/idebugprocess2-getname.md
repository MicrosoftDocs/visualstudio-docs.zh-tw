---
description: 取得進程的標題、易記名稱或檔案名。
title: IDebugProcess2：： GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9817e68cc01c6a867ee2e53a8824ecd759ee014
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081824"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
取得進程的標題、易記名稱或檔案名。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

## <a name="parameters"></a>參數
`gnType`\
在 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 列舉中的值，這個值會指定要傳回的名稱類型。

`pbstrName`\
擴展傳回進程的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
