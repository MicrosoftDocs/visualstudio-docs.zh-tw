---
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdc0dc1155c3ceffa5e784279f113a8c7d30a168
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209062"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
取得本身的連接埠的處理序識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>參數
`pdwProcessId`\
[out]傳回本身的連接埠的實體的處理序識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 在 Win32 執行階段比方說，這個方法通常會呼叫 Win32 函式`GetCurrentProcessId`取得實體的程序識別碼。

## <a name="see-also"></a>另請參閱
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)