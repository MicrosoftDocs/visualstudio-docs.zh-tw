---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95b12c4a5236a401cebbae93b15b69a1d4176ecf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977703"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
此介面可讓偵錯引擎 (DE) 或自訂的連接埠提供者註冊進行偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 Visual Studio 會實作這個介面來註冊，才能顯示偵錯可跨多個處理序偵錯的程式。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫 COM 的`CoCreateInstance`函式搭配`CLSID_ProgramPublisher`來取得這個介面 （請參閱範例）。 DE 或自訂的連接埠提供者會使用此介面，以註冊計劃的節點，代表正在偵錯程式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|讓程式節點使用 DEs 和工作階段偵錯管理員 (SDM)。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程式 節點，使它已無法再使用。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|讓程式使用 DEs 和 SDM。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|移除程式，讓它不再提供。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|設定旗標，指出偵錯工具會出現。|  
  
## <a name="remarks"></a>備註  
 這個介面提供程式和程式節點 （也就是"「 會加以發佈） 使用 DEs 和工作階段的偵錯管理員 (SDM)。 若要存取已發佈的程式和程式節點，請使用[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面。 這是 Visual Studio 可以辨識程式正在偵錯的唯一方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>範例  
 此範例示範如何具現化程式發行者及註冊程式 節點。 這取自教學課程中，[發佈程式節點](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)