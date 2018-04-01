---
title: IDebugField::GetSize |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b6c06a9fd218029c59f2ee004d5c421363530af1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
這個方法會取得欄位，以位元組為單位的大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwSize`  
 [out]傳回的大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 所有欄位都具有型別和所有型別都有大小。 比方說，類型為位元組的欄位有 1 個位元組的大小。  
  
## <a name="see-also"></a>請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)