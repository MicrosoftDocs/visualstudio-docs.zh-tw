---
title: IDebugGeneric場定義 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 019633b62d46f6a8ac68e6f5f4abc888e6986ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728189"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
表示託管代碼泛型類型的欄位的定義。

## <a name="syntax"></a>語法

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|建構給定類型參數陣列的欄位實例。|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|檢索給定參數數的類型參數。|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|檢索與泛型欄位關聯的類型參數數。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
