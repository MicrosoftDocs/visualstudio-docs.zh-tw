---
title: IDebugProgramPublisher2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d49173a4c1f10be1544cf07b0b01640321d6d181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697303"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面可讓 debug engine (DE) 或自訂埠供應商來註冊程式以進行偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Visual Studio 會執行這個介面以註冊要進行偵錯工具的程式，以便在多個進程之間進行跨進程的偵錯工具。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 使用呼叫 COM 的函式 `CoCreateInstance` `CLSID_ProgramPublisher` 來取得此介面 (請參閱範例) 。 DE 或自訂埠供應商會使用此介面來註冊程式節點，以代表要進行偵錯工具的程式。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 此介面會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|使程式節點可供 DEs 和會話 debug manager (SDM) 。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|移除程式節點，使其無法再使用。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|使程式可供 DEs 和 SDM 使用。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|移除程式，使其無法再使用。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|設定旗標，指出偵錯工具存在。|  
  
## <a name="remarks"></a>備註  
 此介面讓程式和程式節點可供使用， (也就是「發佈」它們) 供 DEs 和會話 debug manager (SDM) 使用。 若要存取已發佈的程式和程式節點，請使用 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 介面。 這是 Visual Studio 可以辨識程式正在進行調試的唯一方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>範例  
 此範例示範如何將程式發行者具現化，並註冊程式節點。 這是取自教學 [課程的發行程式節點](https://msdn.microsoft.com/d0100e02-4e2b-4e72-9e90-f7bc11777bae)。  
  
```cpp#  
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
