---
title: IDebugPortRequest2：： GetPortName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724821"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
取得埠的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>參數
`pbstrPortName`\
擴展傳回埠的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)介面通常會從 (用戶端) 傳送到埠供應商的偵錯工具， (伺服器) 取得埠的連接。 Debug 封裝和埠供應商都知道埠的可能選項。 如果簡單字串可以描述埠，則該 `IDebugPortRequest2::GetPortName` 方法有足夠的資訊來進行連接。 否則，用戶端可以提供其他介面，而伺服器可以使用來取得這些介面 `IDebugPortRequest2::QueryInterface` 。

## <a name="see-also"></a>另請參閱
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
