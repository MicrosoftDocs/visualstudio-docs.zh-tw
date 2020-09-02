---
title: IDebugBreakpointChecksumRequest2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d06656ba05c3356d9f2a148045adbf4538c5ae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431604"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

代表中斷點要求的檔總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 由 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debug 封裝所執行，並由偵錯工具引擎使用。  
  
## <a name="methods"></a>方法  
 下表顯示的方法 `IDebugBreakpointChecksumRequest2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|針對指定要使用總和檢查碼演算法的唯一識別碼，抓取中斷點要求的檔總和檢查碼。|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|判斷是否已啟用此檔的總和檢查碼。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
