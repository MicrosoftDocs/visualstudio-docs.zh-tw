---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2349203c49bc164bb3af6bcf51e39afb56022be0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943156"
---
# <a name="idebugalias2"></a>IDebugAlias2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 代表數值的別名的變數，並可讓運算式評估工具 (EE) 來取得應用程式定義域做為別名。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 實作這個介面是由 managed 偵錯引擎 (DE)。  
  
## <a name="methods"></a>方法  
 上的方法除了[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|擷取應用程式定義域的識別項。|  
  
## <a name="remarks"></a>備註  
 別名是十進位的數字，後面接著 # 字元，例如 1001 # 格式為字串。  
  
## <a name="requirements"></a>需求  
 標頭：Ee.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll
