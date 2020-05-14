---
title: IDebug函數物件2::評估 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728441"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
調用函數並將結果值作為物件返回。

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
[在]表示輸入參數的[IDebugObject 物件的](../../../extensibility/debugger/reference/idebugobject.md)陣列。 每個參數都是通過使用此介面中的"創建"方法之一創建的。

`dwParams`\
[在]陣列中的`ppParams`參數數。

`dwEvalFlags`\
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉中的標誌組合,用於指定如何執行計算。

`dwTimeout`\
[在]指定從此方法返回之前等待的最大時間(以毫秒為單位)。 使用**INFINITE**無限期等待。

`ppResult`\
[出]返回表示函數作為物件的值的**IDebugObject。**

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
