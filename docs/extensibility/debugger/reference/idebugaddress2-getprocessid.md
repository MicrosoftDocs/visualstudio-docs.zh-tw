---
title: IDebugAddress2::GetProcessID |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbe84371deb7306300c69f4890398fd43c3061f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099534"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
擷取擁有物件所表示之處理序識別碼[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcID`  
 [out]處理序識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)