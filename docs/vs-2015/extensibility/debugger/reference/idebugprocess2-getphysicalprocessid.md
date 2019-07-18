---
title: IDebugProcess2::GetPhysicalProcessId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 413373dc79ea8e7ed2e5cf1386695896deb96e1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202882"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得系統處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetPhysicalProcessId(  
   AD_PROCESS_ID* pdwProcessId  
);  
```  
  
```csharp  
int GetPhysicalProcessId(  
   AD_PROCESS_ID[] pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwProcessId`  
 [out][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)會填入系統處理序識別碼資訊的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
