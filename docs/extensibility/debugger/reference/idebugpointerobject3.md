---
title: "IDebugPointerObject3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e337fd8d25194dedc467127cce22d383b937e93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示剖析樹狀目錄中的指標，並擴充**IDebugPointerObject**介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具 (EE) 會實作這個介面。  
  
## <a name="methods"></a>方法  
 除了上[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)介面，這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|擷取指標的位址。|  
  
## <a name="requirements"></a>需求  
 標頭： Ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll