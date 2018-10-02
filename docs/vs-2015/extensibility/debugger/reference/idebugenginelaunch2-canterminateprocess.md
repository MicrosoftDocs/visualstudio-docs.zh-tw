---
title: IDebugEngineLaunch2::CanTerminateProcess |Microsoft Docs
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
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5a855da8be95f85abe2f13f32ea6b33228c05dd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488727"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugEngineLaunch2::CanTerminateProcess](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess)。  
  
決定是否會終止處理程序。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示終止程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_FALSE`如果引擎無法終止處理序，比方說，因為存取被拒。  
  
## <a name="remarks"></a>備註  
 如果這個方法會傳回`S_OK`，然後[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)實際結束這個處理序可以呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)

