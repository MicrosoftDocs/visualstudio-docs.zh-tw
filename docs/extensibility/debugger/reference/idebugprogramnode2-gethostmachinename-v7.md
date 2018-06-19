---
title: IDebugProgramNode2::GetHostMachineName_V7 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2adc7125c79afc6b9ebc16b6c4b36f5c147bcdfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115391"
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

## <a name="see-also"></a>另請參閱

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)