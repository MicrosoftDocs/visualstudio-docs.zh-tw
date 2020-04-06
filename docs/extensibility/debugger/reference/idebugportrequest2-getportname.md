---
title: IDebug埠請求2::獲取埠名稱 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724821"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
獲取埠的名稱。

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
[出]返回埠的名稱。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)介面通常從調試包(用戶端)傳遞到埠供應商(伺服器),以獲取到埠的連接。 調試包和埠供應商都瞭解埠的可能選擇。 如果一個簡單的字串可以描述埠,則`IDebugPortRequest2::GetPortName`該方法有足夠的資訊來建立連接。 否則,用戶端可以提供其他介面,伺服器可以使用`IDebugPortRequest2::QueryInterface`獲取這些介面。

## <a name="see-also"></a>另請參閱
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
