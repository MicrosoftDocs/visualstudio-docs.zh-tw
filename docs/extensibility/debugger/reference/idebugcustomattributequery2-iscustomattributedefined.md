---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 619c96a2e38302ff4f40a8376116a67c5664743c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834282"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
判斷名稱是否存在的自訂屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCustomAttributeName`  
 [in]字串，包含要尋找的自訂屬性的名稱。  
  
## <a name="return-value"></a>傳回值  
 會傳回 S_OK 如果自訂屬性定義此欄位中，否則會傳回 S_FALSE。  
  
## <a name="remarks"></a>備註  
 若要取得自訂屬性相關聯的屬性位元組，請呼叫[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)