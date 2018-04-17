---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da6b9c27667ca0960b43ba6e14f0fd4b1fab2634
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
 傳回 S_OK 如果自訂屬性定義此欄位中，否則會傳回 S_FALSE。  
  
## <a name="remarks"></a>備註  
 若要取得自訂屬性相關聯的屬性位元組，請呼叫[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)