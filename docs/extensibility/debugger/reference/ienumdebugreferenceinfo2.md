---
description: 此介面會列舉 DEBUG_REFERENCE_INFO 結構。
title: IEnumDebugReferenceInfo2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89dd664d7b54ce451c2d3a303b3da1c7ad2b13e8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224170"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
此介面會列舉 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構。

## <a name="syntax"></a>Syntax

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會在其支援記憶體中的物件參考時，將此介面實作為其支援。 只有在支援參考時，才必須執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 Visual Studio 會呼叫 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugReferenceInfo2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|抓取列舉序列中指定數目的 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|略過列舉序列中指定數目的 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構。|
|[重設](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|取得枚舉器中 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構的數目。|

## <a name="remarks"></a>備註
 參考基本上是類型和位址，而屬性則是名稱、類型和位址。 只要參考的物件存在於記憶體中，就會保存參考。 如需詳細資訊，請參閱 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
