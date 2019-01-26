---
title: IDebugDocument2::GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 393caa58960795b29abe1389a8f8340643f6c9de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929662"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
取得數種形式之一的文件的名稱。  
  
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
 [in]值，以從[GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)列舉，決定要傳回名稱的類型。  
  
 `pbstrFileName`  
 [out]傳回字串，包含文件名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 為標題或檔案名稱或甚至是檔案名稱的一部分，這個方法可以比方說，會傳回文件的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)