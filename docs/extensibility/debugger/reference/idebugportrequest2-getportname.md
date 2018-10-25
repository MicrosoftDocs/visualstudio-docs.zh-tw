---
title: IDebugPortRequest2::GetPortName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 490381f183a19e33fd391b133562fc2a463c6ee9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920842"
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