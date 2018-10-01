---
title: IDebugProgram2::GetProcess |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5e40776af6011d612d4af79eca70928b6c39edb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498018"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgram2::GetProcess](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getprocess)。  
  
取得此程式正在執行中的程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppProcess`  
 [out]傳回[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)代表程序的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 除非偵錯引擎 (DE) 會實作[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)介面，這個方法 DE 的實作應該一律會傳回`E_NOTIMPL`因為 DE 無法判斷哪個處理序正在執行中，因此無法滿足此方法的實作。  
  
 實作`IDebugEngineLaunch2`介面可讓您表示 DE 必須了解如何建立程序; 因此，DE 實作[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面就能知道它正在中執行哪些處理程序。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

