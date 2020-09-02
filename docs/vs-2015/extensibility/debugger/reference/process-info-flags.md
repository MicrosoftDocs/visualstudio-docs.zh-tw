---
title: PROCESS_INFO_FLAGS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205058"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述或指定進程的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>成員  
 PIFLAG_SYSTEM_PROCESS  
 表示進程是系統進程。  
  
 PIFLAG_DEBUGGER_ATTACHED  
 表示進程正在由偵錯工具進行調試。 它可能是 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 偵錯工具，也可能是一些其他偵錯工具，例如 WinDbg。  
  
 PIFLAG_PROCESS_STOPPED  
 表示進程已停止。 只有 `PIFLAG_DEBUGGER_ATTACHED` 在同時指定時才有效。 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 和更新版本中提供。  
  
 PIFLAG_PROCESS_RUNNING  
 表示進程正在執行中。 只有 `PIFLAG_DEBUGGER_ATTACHED` 在同時指定時才有效。 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 和更新版本中提供。  
  
## <a name="remarks"></a>備註  
 用於 `Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 結構的成員。  
  
 這些旗標可以與位結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
