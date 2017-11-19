---
title: "STEPUNIT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STEPUNIT
helpviewer_keywords: STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0f4dab5124e3f7d6924c5f02f552832e8b0fd36
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="stepunit"></a>STEPUNIT
逐步執行步驟單位指定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>成員  
 STEP_STATEMENT  
 由陳述式的步驟。  
  
 STEP_LINE  
 所列的步驟。  
  
 STEP_INSTRUCTION  
 依指示的步驟。  
  
## <a name="remarks"></a>備註  
 做為引數傳遞[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)