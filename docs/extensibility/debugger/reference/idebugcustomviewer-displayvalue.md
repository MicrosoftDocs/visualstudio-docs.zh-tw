---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c374cfa79b91d70895f94be4f1c3f28c5ac4c02
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205164"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
顯示指定的值，會呼叫這個方法。

## <a name="syntax"></a>語法

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>參數
`hwnd`\
[in]父視窗

`dwID`\
[in]支援多個類型的自訂檢視器的識別碼。

`pHostServices`\
[in] 保留。 一律設為 null。

`pDebugProperty`\
[in]介面，可用來擷取要顯示的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會建立必要的視窗、 顯示值、 等待輸入，並關閉視窗，所有傳回給呼叫端之前，顯示是"modal"。 這表示此方法必須處理的顯示屬性的值，無法建立輸出，以等候使用者輸入，若要終結視窗的視窗的所有層面。

 若要支援上變更值，指定[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)物件，您可以使用[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法： 如果此值可以表示為字串。 否則，就必須建立自訂的介面 — 獨佔運算式評估工具實作此`DisplayValue`方法，實作的相同物件上`IDebugProperty3`介面。 這個自訂的介面會提供方法來變更資料的任意規模或複雜度。

## <a name="see-also"></a>另請參閱
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)