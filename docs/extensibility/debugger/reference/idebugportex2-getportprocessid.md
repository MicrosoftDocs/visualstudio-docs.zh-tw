---
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 3d3a3e1b8eb97d627fa94ff6d5bb153355df7b41
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Gets the process ID of the port itself.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```cs  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pdwProcessId`  
 [out] Returns the physical process ID of the port itself.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 In the Win32 runtime for example, this method typically calls the Win32 function `GetCurrentProcessId` to get the physical process ID.  
  
## <a name="see-also"></a>See Also  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
