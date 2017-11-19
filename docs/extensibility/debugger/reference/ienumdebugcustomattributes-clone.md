---
title: "IEnumDebugCustomAttributes::Clone |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Clone
helpviewer_keywords: IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16ac30382492525333756f297587fed8458ff57b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
建立列舉值，包含目前的列舉值的列舉型別狀態相同。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone (   
   IEnumCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppEnum  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的副本會呼叫這個方法只有在有相同的原始狀態。 不過，複製和原始的狀態分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)