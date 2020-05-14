---
title: IDebugCoreServer3::創建實例伺服器 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733013"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
在伺服器上創建調試引擎的實例。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>參數
`szDll`\
[在]實現參數中指定的 CLSID 的`clsidObject`dll 的路徑。 如果是`NULL`,則調用`CoCreateInstance`COM 函數。

`wLangId`\
[在]調試引擎區域設置。 如果不應調用[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)方法,則此方法可以是 0。

`clsidObject`\
[在]要建立的除錯引擎的 CLSID。

`riid`\
[在]要從類物件檢索的特定介面的介面 ID。

`ppvObject`\
[出]`IUnknown`來自實例化物件的介面。 強制轉換或封送此物件到所需的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
