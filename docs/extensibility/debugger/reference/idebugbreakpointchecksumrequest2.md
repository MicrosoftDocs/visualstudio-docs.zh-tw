---
title: "IDebugBreakpointChecksumRequest2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 080d9178889593e22f19b64fe2c60da370dcc3f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
表示中斷點要求的文件總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯封裝，且由偵錯引擎。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugBreakpointChecksumRequest2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|擷取的中斷點要求指定總和檢查碼演算法的唯一識別項使用的文件總和檢查碼。|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|判斷是否啟用此文件的總和檢查碼。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll