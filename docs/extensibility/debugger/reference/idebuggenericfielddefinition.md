---
title: IDebugGenericFieldDefinition |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ff7c28a30ccab43629636f7dcd9391a669a376ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884789"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
代表 managed 程式碼泛型型別的欄位定義。

## <a name="syntax"></a>Syntax

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|在給定型別引數的陣列時，建立欄位實例。|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|根據參數數目來抓取類型參數。|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|抓取與泛型欄位相關聯之類型參數的數目。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
