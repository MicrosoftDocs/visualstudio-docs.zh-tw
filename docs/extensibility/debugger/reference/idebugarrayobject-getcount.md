---
title: "IDebugArrayObject::GetCount |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetCount
helpviewer_keywords: IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 00f3f0daa09f41168224c0d0817707de26dc817a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
陣列中取得的項目計數。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwElements`  
 [out]傳回計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將所有項目的陣列物件視為一維陣列，即使多維陣列物件。 例如，假設陣列`myarray[3][2][6]`，這個方法會傳回在 36`pdwElements`參數。 使用[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法來擷取一次一個的個別項目。  
  
## <a name="see-also"></a>請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)