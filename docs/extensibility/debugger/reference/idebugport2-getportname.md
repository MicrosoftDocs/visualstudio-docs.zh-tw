---
title: IDebugPort2::GetPortName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortName
helpviewer_keywords:
- IDebugPort2::GetPortName
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c450042f1bd2ef9199c8752f231b638487625ab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914510"
---
# <a name="idebugport2getportname"></a>IDebugPort2::GetPortName
取得的連接埠名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrName`  
 [out]傳回的連接埠的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)