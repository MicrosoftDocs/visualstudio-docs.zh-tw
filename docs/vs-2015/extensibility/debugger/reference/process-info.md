---
title: PROCESS_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205012"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

包含處理常式的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>成員  
 欄位  
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)列舉中的旗標組合，可指定要填寫的欄位。  
  
 bstrFileName  
 進程的完整路徑名稱。 相當於使用參數呼叫 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 方法 `GN_FILENAME` 。  
  
 bstrBaseName  
 進程的檔案名和副檔名。 相當於呼叫 `IDebugProcess2::Getname` 具有參數的方法 `GN_BASENAME` 。  
  
 bstrTitle  
 進程的標題（如果有的話）。 相當於呼叫 `IDebugProcess2::Getname` 具有參數的方法 `GN_TITLE` 。  
  
 ProcessId  
 識別進程的 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構。 相當於呼叫 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) 方法。  
  
 dwSessionId  
 此進程正在其中執行之 debug 會話的識別碼。  
  
 bstrAttachedSessionName  
 附加的會話名稱。 相當於呼叫 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) 方法。  
  
 CreationTime  
 進程的建立時間。  
  
 Flags  
 指定進程屬性之 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) 列舉中的旗標組合。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至其填入的 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
