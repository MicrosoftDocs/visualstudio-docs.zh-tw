---
title: GETHOSTNAME_TYPE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97e252f9f7b3d3177b099e98984ee459b85f0c82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823056"
---
# <a name="gethostnametype"></a>GETHOSTNAME_TYPE
指定主機名稱的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## <a name="members"></a>成員  
 GHN_FRIENDLY_NAME  
 指定主應用程式的易記名稱。  
  
 GHN_FILE_NAME  
 指定主機的檔案名稱。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞做為引數[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法來擷取主機名稱格式不同。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)