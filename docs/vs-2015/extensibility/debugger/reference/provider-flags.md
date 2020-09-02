---
title: PROVIDER_FLAGS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c39aa316308f313bf23ef2c5680671585636f0a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204944"
---
# <a name="provider_flags"></a>PROVIDER_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要從程式提供者取得的所需屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
typedef DWORD PROVIDER_FLAGS;  
```  
  
```csharp  
public enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
```  
  
## <a name="members"></a>成員  
 PFLAG_NONE  
 未指定旗標。  
  
 PFLAG_REMOTE_PORT  
 呼叫端需要不同電腦上的程式清單，而不是 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。  
  
 PFLAG_DEBUGGEE  
 此進程目前正在由此的實例進行調試 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。  
  
 PFLAG_ATTACH_TODEBUGGEE  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 附加至正在進行調試但未啟動的程式。  
  
 PFLAG_REASON_WATCH  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 正在監看事件。  
  
 PFLAG_GET_PROGRAM_NODES  
 呼叫端想要 `ProgramNodes` [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 結構的欄位。  
  
 PFLAG_GET_IS_DEBUGGER_PRESENT  
 呼叫端需要 `fIsTheDebuggerPresent` 結構的欄位 `PROVIDER_PROCESS_DATA` 。  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞至下列方法：  
  
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
  這些值可以與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
