---
title: "PROCESS_INFO_FLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FLAGS
helpviewer_keywords: PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 228b2d3286ad0b69a2eb813e18b8837ec038f28f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
描述或指定的處理程序的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>成員  
 PIFLAG_SYSTEM_PROCESS  
 表示處理程序是系統處理序。  
  
 PIFLAG_DEBUGGER_ATTACHED  
 表示處理程序正在偵錯的偵錯工具。 它可能是[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具，或者它可能是某些其他偵錯工具，例如 WinDbg。  
  
 PIFLAG_PROCESS_STOPPED  
 表示已停止處理程序。 只有才有效`PIFLAG_DEBUGGER_ATTACHED`同時指定。 用於[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]和更新版本。  
  
 PIFLAG_PROCESS_RUNNING  
 指出處理序正在執行。 只有才有效`PIFLAG_DEBUGGER_ATTACHED`同時指定。 用於[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]和更新版本。  
  
## <a name="remarks"></a>備註  
 用於`Flags`隸屬[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)結構。  
  
 這些旗標可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)