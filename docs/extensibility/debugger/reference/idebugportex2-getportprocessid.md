---
title: IDebugPortEx2::獲取埠處理Id |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae974461e312c68e6fcc14150a08879ac7709950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725146"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
獲取埠本身的進程 ID。

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
[出]返回埠本身的物理進程 ID。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 例如,在 Win32 執行時中,此方法通常調用`GetCurrentProcessId`Win32 函數來獲取物理進程 ID。

## <a name="see-also"></a>另請參閱
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
