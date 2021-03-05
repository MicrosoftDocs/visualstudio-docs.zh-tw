---
description: IDebugFunctionObject2：：評估會呼叫函數，並傳回產生的值做為物件。
title: IDebugFunctionObject2：：評估 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 777553e1889e751cf84f6e4c58691e0c5f446648
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166459"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
呼叫函數，並傳回產生的值做為物件。

## <a name="syntax"></a>語法

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>參數
`ppParams`\
在 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件的陣列，表示輸入參數。 這些參數都是使用這個介面中的其中一個 Create 方法來建立。

`dwParams`\
在陣列中的參數數目 `ppParams` 。

`dwEvalFlags`\
在 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 列舉中的旗標組合，指定評估的執行方式。

`dwTimeout`\
在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 **無限** 期等候無限期等候。

`ppResult`\
擴展傳回 **IDebugObject** ，表示函式的值做為物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
