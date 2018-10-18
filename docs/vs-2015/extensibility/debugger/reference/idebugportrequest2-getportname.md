---
title: IDebugPortRequest2::GetPortName |Microsoft Docs
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
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11097133a3f37058e71ed81a1dd73b71480f27e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185441"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得連接埠的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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

