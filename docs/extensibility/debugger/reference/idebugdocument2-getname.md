---
title: IDebugDocument2::GetName |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2eeef7ced30d6f8de3b9d0fc6f783502936a4859
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
取得其中一種數種形式的文件的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `gnType`  
 [in]中的值[GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)列舉，可判斷要傳回名稱的類型。  
  
 `pbstrFileName`  
 [out]傳回字串，包含文件名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 為標題或檔案名稱或甚至是檔案名稱的一部分，這個方法可以比方說，會傳回文件的名稱。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)