---
title: "IDebugField::GetInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetInfo
helpviewer_keywords: IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ff061a73de70918480450ea8763f9eea2fc34cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
這個方法會取得的欄位可顯示的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]組合[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)選取要顯示資訊的常數。 如果欄位代表一個符號，這通常是符號名稱和型別。  
  
 `pFieldInfo`  
 [out]傳回中所提供的資訊[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)