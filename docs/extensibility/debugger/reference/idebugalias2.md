---
title: IDebugAlias2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15fbf639c15e62b19e112ad140517f096d49f9d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 代表數值的別名變數，並可讓運算式評估工具 (EE) 以取得應用程式定義域做為別名。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這個介面是由 managed 偵錯引擎 (DE) 實作。  
  
## <a name="methods"></a>方法  
 除了上[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|擷取應用程式定義域的識別項。|  
  
## <a name="remarks"></a>備註  
 別名是後面接著 # 字元，例如 1001 # 字串形式的十進位數字。  
  
## <a name="requirements"></a>需求  
 標頭： Ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll