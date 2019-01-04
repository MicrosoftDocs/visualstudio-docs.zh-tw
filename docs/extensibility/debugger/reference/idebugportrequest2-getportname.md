---
title: IDebugPortRequest2::GetPortName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c916e379c5a5f3f50fbad8d6b38548f2b0603eff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940131"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
取得連接埠的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrPortName`  
 [out]傳回的連接埠的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)介面通常會傳遞從偵錯封裝 （用戶端） 以取得連線的連接埠提供者 （伺服器） 的連接埠。 偵錯套件和連接埠提供者會留意可能的選項，為連接埠。 如果一個簡單的字串可以描述為連接埠，則`IDebugPortRequest2::GetPortName`方法具有足夠的資訊來進行連線。 否則其他介面可提供用戶端，可以取得伺服器使用`IDebugPortRequest2::QueryInterface`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)