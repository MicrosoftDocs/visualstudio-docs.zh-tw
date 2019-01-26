---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0228d718377f6bd43ae44b44fb44900e4526d3b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990702"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> 已被取代。 請勿使用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>參數

`pbstrHostMachineName`  
[out]傳回在其中執行程式的電腦名稱。

## <a name="return-value"></a>傳回值

實作應該一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 截至 Visual Studio 2005 中，這個方法不會再使用，並應該一律傳回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)