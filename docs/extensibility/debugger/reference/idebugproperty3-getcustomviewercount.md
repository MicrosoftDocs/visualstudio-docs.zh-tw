---
title: IDebug屬性3::獲取自定義查看器計數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16cb623f58668362e5e308e1d66dfd6ca7c0fb8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721192"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
獲取可能可用於此屬性的自定義查看器數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>參數
`pcelt`\
[出]可用於此屬性的自定義查看器數。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
為了支援類型視覺化工具,此方法將呼叫到[GetCustomViewerCount 方法](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)。 如果表示式賦值器還支援此屬性類型的自定義查看器,則此方法會將自定義查看器的數量添加到返回的值。

有關類型視覺化器和自訂檢視器之間的差異的詳細資訊,請參閱[類型視覺化器和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面的**CProperty**物件實現此方法。

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>另請參閱
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
