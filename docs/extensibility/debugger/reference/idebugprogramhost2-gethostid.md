---
title: IDebugProgramHost2::GetHostId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74e4575eca8a9f67446a60737c051a574109b97e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831096"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
取得裝載此程式的處理序的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```csharp  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwId`  
 [in、 out][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)會填入的處理序識別項資訊的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)