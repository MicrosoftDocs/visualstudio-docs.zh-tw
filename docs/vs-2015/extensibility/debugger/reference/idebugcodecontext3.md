---
title: IDebugCodeCoNtext3 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62b84bd77038c7a17b65f764bd303d6a6372a52c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154159"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擴充 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 介面，以啟用模組和進程介面的抓取。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 由 debug 引擎所執行，並由 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debug 封裝使用。  
  
## <a name="methods"></a>方法  
 除了介面上的方法 `IDebugCodeContext2` ，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|抓取 debug 模組的介面參考。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|抓取對 debug 進程介面的參考。|  
  
## <a name="remarks"></a>備註  
 這是選擇性的介面，通常不需要執行。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
