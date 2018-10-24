---
title: ASSEMBLYLOCRESOLUTION |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dd26c46e6725ca34f6b1da69127785bf57956b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885005"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定組件所在的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## <a name="members"></a>成員  
 ALR_NAME  
 組件位於目前的命名空間中。  
  
 ALR_USERDIR  
 組件位於使用者目錄中。  
  
 ALR_SHAREDDIR  
 組件位於共用目錄。  
  
 ALR_REMOTEDIR  
 組件位於遠端目錄。  
  
## <a name="remarks"></a>備註  
 這些值會傳回[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)並[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)方法。  
  
 這些值可以結合`OR`作業。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)

