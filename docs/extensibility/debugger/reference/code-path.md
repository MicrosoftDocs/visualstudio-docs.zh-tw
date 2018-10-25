---
title: CODE_PATH |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9618d28aeadaa85d97e9018fdf57ee8952ac3fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920257"
---
# <a name="codepath"></a>CODE_PATH
描述的方法或函式的呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>成員  
 bstrName  
 程式碼路徑的名稱。  
  
 pCode  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)其中逐步執行函式程式碼中識別的物件。  
  
## <a name="remarks"></a>備註  
 此結構用來實作逐步執行函式。 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)從目前的位置中正在偵錯程式會傳回所有的呼叫。 這個結構是表示一個這類呼叫。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)