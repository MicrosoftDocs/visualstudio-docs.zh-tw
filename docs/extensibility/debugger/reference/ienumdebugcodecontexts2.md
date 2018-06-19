---
title: IEnumDebugCodeContexts2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc6ff9a173bcfbb87606fe493697857d7ec2b323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122557"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
這個介面會列舉與偵錯工作階段中，或特定的程式或文件相關聯的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表在程式中，特定的文字位置的程式碼內容的清單或一份特定文件內容的程式碼內容。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)取得此介面代表該應用程式的來源文件中的特定文字位置的程式碼內容的清單。  
  
 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)取得此介面代表特定的來源文件中的所有程式碼內容的清單。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugCodeContexts2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|擷取指定的數目的列舉順序中的程式碼內容。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|略過指定的數目的列舉順序中的程式碼內容。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|列舉中取得的程式碼內容的數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)填入的程式碼內容的清單，使用者可以選擇從時設定下一個陳述式，或顯示反組譯碼的原始程式檔。 多個程式碼的內容可能發生，例如，當有多個 c + + 樣式範本執行個體。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)