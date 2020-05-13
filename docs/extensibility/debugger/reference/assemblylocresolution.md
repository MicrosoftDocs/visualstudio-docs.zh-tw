---
title: 程式集解析度 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbd015408cbefd1861f6e795447a5302efabb0dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738134"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
指定程式集的位置。

## <a name="syntax"></a>語法

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>欄位
`ALR_NAME`\
程式集位於目前命名空間中。

`ALR_USERDIR`\
程式集位於使用者目錄中。

`ALR_SHAREDDIR`\
程式集位於共用目錄中。

`ALR_REMOTEDIR`\
程式集位於遠端目錄中。

## <a name="remarks"></a>備註
這些值由[解析程式集Ref](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)和[獲取託管檢視器創建資料](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)方法返回。

這些值可以與操作的結合`OR`使用 。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
