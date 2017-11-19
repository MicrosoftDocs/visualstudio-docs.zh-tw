---
title: "IDebugEngine2::SetMetric |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2:::SetMetric
helpviewer_keywords: IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 125cedb79be629e6024e90afef16b34e57d94571
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
這個方法會設定稱為度量資訊的登錄值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszMetric`  
 [in]度量的名稱。  
  
 `varValue`  
 [in]指定度量的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 度量資訊是用來變更偵錯引擎的行為，或廣告支援的功能的登錄值。 這個方法可以將呼叫轉送至適當的形式[SDK 進行偵錯的協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函式， `SetMetric`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)