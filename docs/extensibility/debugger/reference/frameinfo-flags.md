---
title: FRAMEINFO_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a7db578a057f788bf64c1444ceb406cc11ff847
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928405"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
指定要擷取的堆疊框架物件有關的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>成員  
 FIF_FUNCNAME  
 初始化/使用`m_bstrFuncName`欄位。  
  
 FIF_RETURNTYPE  
 初始化/使用`m_bstrReturnType`欄位。  
  
 FIF_ARGS  
 初始化/使用`m_bstrArgs`欄位。  
  
 FIF_LANGUAGE  
 初始化/使用`m_bstrLanguage`欄位。  
  
 FIF_MODULE  
 初始化/使用`m_bstrModule`欄位。  
  
 FIF_STACKRANGE  
 初始化/使用`m_addrMin`和`m_addrMax`（堆疊範圍） 欄位。  
  
 FIF_FRAME  
 初始化/使用`m_pFrame`欄位。  
  
 FIF_DEBUGINFO  
 初始化/使用`m_fHasDebugInfo`欄位。  
  
 FIF_STALECODE  
 初始化/使用`m_fStaleCode`欄位。  
  
 FIF_ANNOTATEDFRAME  
 初始化/使用`m_fAnnotatedFrame`欄位。  
  
 FIF_DEBUG_MODULEP  
 初始化/使用`m_pModule`欄位。  
  
 FIF_FUNCNAME_FORMAT  
 格式函式名稱。 在傳回的結果`m_bstrFunName`欄位和任何其他欄位會填入。  
  
 FIF_FUNCNAME_RETURNTYPE  
 將傳回的型別以`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS  
 將加入的引數`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_LANGUAGE  
 新增的語言`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_MODULE  
 將模組名稱來`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_LINES  
 新增的行數`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_OFFSET  
 將加入至`m_bstrFuncName`欄位從行開頭的位元組位移，如果`FIF_FUNCNAME_LINES`指定。 如果`FIF_FUNCNAME_LINES`未指定，或如果沒有可用的行號，以位元組為單位將位移從函式的開頭。  
  
 FIF_FUNCNAME_ARGS_TYPES  
 將每個函式引數的類型加入`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_NAMES  
 新增至每個函式引數名稱`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_VALUES  
 將每個函式引數的值加入`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_ALL  
 將型別、 名稱和值的所有引數`m_bstrFuncName`欄位。  
  
 FIF_ARGS_TYPES  
 引數類型會擷取並格式化。  
  
 FIF_ARGS_NAMES  
 引數名稱會擷取並格式化。  
  
 FIF_ARGS_VALUES  
 將引數值會擷取並格式化。  
  
 FIF_ARGS_ALL  
 擷取並格式化型別、 名稱和所有的引數的值。  
  
 FIF_ARGS_NOFORMAT  
 指定不格式化的引數 （例如，進行不加入開啟和關閉前後的引數清單括號也新增引數之間的分隔符號）。  
  
 FIF_ARGS_NO_FUNC_EVAL  
 指定擷取引數的值時，不應該使用函式 （屬性） 評估。  
  
 FIF_FILTER_NON_USER_CODE  
 偵錯引擎是篩選非使用者程式碼框架，因此它們都不包含。  
  
 FIF_ARGS_NO_TOSTRING  
 不允許`ToString()`函式評估或格式傳回函式引數時。  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 從裝載的應用程式定義域，而不是裝載處理序，就應該取得框架資訊。  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞給[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)並[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法以指出哪些欄位是在初始化[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。  
  
 這些旗標也可用來表示欄位[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構會使用和有效時，會傳回這個結構。 這些值可能會合併的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)