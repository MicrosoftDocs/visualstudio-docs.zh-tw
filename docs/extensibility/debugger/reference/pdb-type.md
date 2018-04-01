---
title: PDB_TYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f1c08df8cf56d81ebb22fbdf17f3d20084599b51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="pdbtype"></a>PDB_TYPE
此結構會指定取自 PDB 符號的欄位類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>參數  
 ulAppDomainID  
 應用程式的來源符號的識別碼。 這用來唯一識別應用程式的執行個體。  
  
 guidModule  
 包含此欄位之模組的 GUID。  
  
 symid  
 此欄位的對應符號的識別碼。  
  
## <a name="remarks"></a>備註  
 此結構會顯示過程中的等位[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位`TYPE_INFO`結構設為`TYPE_KIND_PDB`(介於[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別）。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)