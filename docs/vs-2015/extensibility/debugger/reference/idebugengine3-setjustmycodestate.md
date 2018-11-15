---
title: IDebugEngine3::SetJustMyCodeState |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc701306166cacc1eb25881fee090c91af069589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818025"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會告知偵錯引擎的 JustMyCode 狀態資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fUpdate`  
 [in]非零值 (`TRUE`) 來更新目前的資訊，請為零 (`FALSE`) 重設 （忽略任何先前設定） 的所有資訊。  
  
 `dwModules`  
 [in]中的資訊結構數目 `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in]陣列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)若要使用的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 JustMyCode 是屬於使用者程式碼偵錯，並忽略所有的中繼程式碼，例如系統程式碼的概念，即使原始程式碼是適用於該系統程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)

