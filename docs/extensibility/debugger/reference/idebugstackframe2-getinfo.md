---
title: IDebugStackFrame2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0aeb888b2cc81dac6157ef0944703227799e61e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721013"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
取得堆疊框架的描述。

## <a name="syntax"></a>語法

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

#### <a name="parameters"></a>參數
 `dwFieldSpec`

 [in]從旗標的組合[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉，指定哪些欄位`pFrameInfo`參數是要填入。

 `nRadix`

 [in]要用於格式化數字的任何資訊基數。

 `pFrameInfo`

 [out]A [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構，其中會填入的堆疊框架的描述。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)