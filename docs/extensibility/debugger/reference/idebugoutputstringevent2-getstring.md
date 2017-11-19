---
title: "IDebugOutputStringEvent2::GetString |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugOutputStringEvent2::GetString
helpviewer_keywords: IDebugOutputStringEvent2::GetString
ms.assetid: f059f8e0-ad44-49ac-ba90-73576ada5e06
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d00c14c120aa282ce36de3a16db91029c1e08c99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugoutputstringevent2getstring"></a>IDebugOutputStringEvent2::GetString
取得可顯示的訊息。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetString(   
   BSTR* pbstrString  
);  
```  
  
```csharp  
int GetString(   
   out string pbstrString  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrString`  
 [out]傳回可顯示的訊息。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)