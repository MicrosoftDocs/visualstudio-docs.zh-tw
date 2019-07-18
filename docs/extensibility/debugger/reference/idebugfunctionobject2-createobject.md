---
title: IDebugFunctionObject2::CreateObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87d1c2cd71b57136e26a2bc30004547dc4b8dee5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313417"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
建立會使用指定評估旗標設定和逾時值的建構函式的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>參數
`pConstructor`\
[in][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件，表示要建立之物件的建構函式。

`dwArgs`\
[in]中的參數數目`pArg`陣列。 表示傳遞至建構函式的參數數目。

`pArgs`\
[in]陣列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，表示的參數傳遞至建構函式。

`dwEvalFlags`\
[in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉，指定要如何進行評估。

`dwTimeout`\
[in]最大時間 （毫秒），這個方法返回之前等候。 使用**無限**無限期等候。

`ppObject`\
[out]傳回**IDebugObject**代表新建立的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法來建立物件，表示類別或其他需要的建構函式，為參數的複雜類型的執行個體。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)