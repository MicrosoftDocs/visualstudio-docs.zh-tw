---
title: IDebug提供程式程序節點2::取消封送調試介面 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720712"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
獲取跨進程邊界的指定介面。

## <a name="syntax"></a>語法

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>參數
`riid`\
[在]要獲取的介面的 GUID。

`ppvObject`\
[出]返回實現所需介面的物件。 [C++] 可以直接轉換為所需的介面類型。 [C]<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>使用 方法獲取所需的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當調試引擎在[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]進程空間中運行時,並且正在調試的程式在其自己的進程空間中運行時,將使用此方法。

## <a name="see-also"></a>另請參閱
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
