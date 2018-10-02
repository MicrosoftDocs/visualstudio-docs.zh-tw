---
title: IDebugProgram2::Terminate |Microsoft Docs
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
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05edc99dcb408159966f08a3d38f6663f73f290
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491104"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgram2::Terminate](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-terminate)。  
  
終止程式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式可能的話，會終止並從處理序; 卸載否則，偵錯引擎 (DE) 會執行任何必要的清除作業。  
  
 這個方法或[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) IDE，通常以回應中止所有偵錯使用者所呼叫方法。 此方法的實作應該在理想情況下，終止處理序內的程式。 如果這不可行，DE 應該防止程式執行此程序更多 （並執行任何必要的清除）。 如果`IDebugProcess2::Terminate`由 IDE 所呼叫的方法，整個程序將會終止一段時間之後`IDebugProgram2::Terminate`呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

