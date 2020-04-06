---
title: DEBUG_CUSTOM_VIEWER |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737540"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
標識自定義查看器或類型可視化工具的結構。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>成員
`dwID`\
一個 ID,用於區分由一`GUID`個 實現的多個檢視器或可視化工具。

`bstrMenuName`\
下拉選單中顯示的文本。

`bstrDescription`\
自定義查看器或類型可視化工具的說明(如果未使用,則必須是空值)。

`guidLang`\
提供表達式賦值器的語言。

`guidVendor`\
提供表達式賦值器的供應商。

`bstrMetric`\
存儲自定義查看器或類型可視化工具`CLSID`的指標。

## <a name="remarks"></a>備註
此結構的清單通過調用[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法(以及通過擴展[返回 GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法)返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
