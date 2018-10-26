---
title: EncUnavailableReason |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8228d741848ba90c2d2d39618781e6d915c4b627
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854646"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 表示的原因，**編輯後繼續**不提供。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>參數  
 ENCUN_NONE  
 沒有特定的理由為何無法使用 編輯後繼續。  
  
 ENCUN_INTEROP  
 編輯後繼續不提供 InterOp 呼叫期間。  
  
 ENCUN_SQLCLR  
 編輯後繼續提供期間不會使用 Common Language Runtime (CLR) 的 SQL 程序呼叫。  
  
 ENCUN_MINIDUMP  
 編輯後繼續不提供在處理小型傾印。  
  
 ENCUN_EMBEDDED  
 編輯後繼續使用時不處理內嵌程式碼。  
  
 ENCUN_ATTACH  
 編輯後繼續 無法使用工作階段已附加到，因為無法啟動的偵錯工具。  
  
 ENCUN_WIN64  
 編輯後繼續不提供處理 64 位元 Windows 程式碼時。  
  
## <a name="remarks"></a>備註  
 這個列舉僅供內部使用由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)並[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法所實作的自訂連接埠供應商應該一律會傳回`E_NOTIMPL`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.idl  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)