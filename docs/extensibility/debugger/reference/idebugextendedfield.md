---
title: IDebugExtendedField |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eedb327e19d012c653a9a5411c0ba7f1924cb369
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
擴充欄位，皆可支援 managed 程式碼的泛型的類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>方法  
 除了上[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|擷取指定的擴充的欄位類型。|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|決定是否表示封閉的類型欄位。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll