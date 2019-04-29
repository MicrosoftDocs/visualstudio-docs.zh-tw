---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b80afe3f0061e016301b86229f2eacedf217a43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870111"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
終止程式。

## <a name="syntax"></a>語法

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 程式可能的話，會終止並從處理序; 卸載否則，偵錯引擎 (DE) 會執行任何必要的清除作業。

 這個方法或[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) IDE，通常以回應中止所有偵錯使用者所呼叫方法。 此方法的實作應該在理想情況下，終止處理序內的程式。 如果這不可行，DE 應該防止程式執行此程序更多 （並執行任何必要的清除）。 如果`IDebugProcess2::Terminate`由 IDE 所呼叫的方法，整個程序將會終止一段時間之後`IDebugProgram2::Terminate`呼叫方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)