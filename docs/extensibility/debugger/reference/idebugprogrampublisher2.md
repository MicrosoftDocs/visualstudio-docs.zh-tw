---
title: IDebugProgramPublisher2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 20f5fe710cc05425263245c9a78ff804aca2ac20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
這個介面可讓偵錯引擎 (DE) 或自訂連接埠供應商註冊進行偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 實作此介面，以便註冊才能讓變更可見的偵錯可跨多個處理序偵錯的程式。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫 COM 的`CoCreateInstance`函式與`CLSID_ProgramPublisher`取得此介面 （請參閱範例）。 DE 或自訂連接埠供應商使用此介面來註冊程式節點代表偵錯的程式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|讓程式節點使用 DEs 和工作階段偵錯管理員 (SDM)。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程式 節點，所以已無法再使用。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|讓程式使用 DEs 和 SDM。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|移除程式，因此已無法再使用。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|設定旗標，表示偵錯工具已存在。|  
  
## <a name="remarks"></a>備註  
 這個介面提供的程式和程式的節點 （也就是 「 發行 」 它們） DEs 和工作階段的偵錯管理員 (SDM) 所使用。 若要存取已發行的程式和程式節點時，使用[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面。 這是 Visual Studio 可辨識的偵錯程式的唯一方式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>範例  
 這個範例示範如何具現化程式發行者及註冊程式節點。 這取自教學課程中，[發佈程式節點](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae)。  
  
```cpp  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)