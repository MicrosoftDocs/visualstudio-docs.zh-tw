---
title: "IDebugProperty2::GetReference |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetReference
helpviewer_keywords: IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c72b1d968cab7f320046ea9eb82a4a7c1fea543d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
傳回屬性值的參考。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```csharp  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppRererence`  
 [out]傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)代表屬性的值參考的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回的錯誤代碼，通常`E_NOTIMPL`或`E_GETREFERENCE_NO_REFERENCE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)