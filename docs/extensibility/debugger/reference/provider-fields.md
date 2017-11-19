---
title: "PROVIDER_FIELDS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_FIELDS
helpviewer_keywords: PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01aa9048e26c265b1fe04ba653fb224b86ec77cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="providerfields"></a>PROVIDER_FIELDS
指定程式提供者相關聯的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>成員  
 PFIELD_PROGRAM_NODES  
 `ProgramNodes`欄位無效。  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 `fIsDebuggerPresent`欄位無效。  
  
## <a name="remarks"></a>備註  
 這些值會傳回`Fields`隸屬[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構表示明確填入結構的哪些欄位。  
  
 這些值可以合併的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)