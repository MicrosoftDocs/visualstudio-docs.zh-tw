---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef26af92dd50d4d79dc2f48e8cd7e32c03e86702
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
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
[out]傳回程式正在執行的電腦名稱。

## <a name="return-value"></a>傳回值

實作應該會一律傳回`E_NOTIMPL`。

## <a name="remarks"></a>備註

> [!WARNING]
> 自 Visual Studio 2005 中，這個方法已不再使用，應該會一律傳回`E_NOTIMPL`。

## <a name="see-also"></a>請參閱

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)