---
description: 識別自訂檢視器或型別視覺化的結構。
title: DEBUG_CUSTOM_VIEWER |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46133d2b2800977b0819835f578b04569c4f5ce8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151053"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
識別自訂檢視器或型別視覺化的結構。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>成員
`dwID`\
用來區別多個由一個檢視器或視覺化程式所執行的識別碼 `GUID` 。

`bstrMenuName`\
將會出現在下拉式功能表中的文字。

`bstrDescription`\
如果未使用) ，則 [自訂檢視器] 或 [類型] 視覺化 (的描述必須為 null 值。

`guidLang`\
提供運算式評估工具的語言。

`guidVendor`\
提供運算式評估工具的廠商。

`bstrMetric`\
用來儲存自訂檢視器或類型視覺化的度量 `CLSID` 。

## <a name="remarks"></a>備註
呼叫 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法時，會傳回這個結構的清單 (以及 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 方法) 的擴充方法。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
