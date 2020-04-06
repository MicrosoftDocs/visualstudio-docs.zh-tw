---
title: IDebugField:獲取擴展資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728872"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
此方法獲取有關欄位的擴展資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>參數
`guidExtendedInfo`\
[在]選擇要返回的資訊。 有效值為：

|值|描述|
|-----------|-----------------|
|`guidConstantValue`|值作為位元組序列。|
|`guidConstantType`|類型作為類型簽名。|

`prgBuffer`\
[出]返回擴展的資訊。

`pdwLen`\
[進出]返回擴展資訊的大小(以位元組為單位)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 目前,此方法僅返回常量的類型或值。 呼叫方必須透過呼叫 COM`prgBuffer`的函數 (C++)`CoTaskMemFree`或<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>(C#) 釋放傳回的緩衝區。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
