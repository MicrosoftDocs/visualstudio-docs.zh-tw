---
title: IDebugPort供應商描述2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724363"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
使[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 能夠在 **「附加到流程」** 對話框的 **「傳輸資訊**」部分內顯示文本。

## <a name="syntax"></a>語法

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由埠供應商實現。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugPortSupplierDescription2`。

|方法|描述|
|------------|-----------------|
|[取得描述](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|檢索埠供應商的說明和描述元數據。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
