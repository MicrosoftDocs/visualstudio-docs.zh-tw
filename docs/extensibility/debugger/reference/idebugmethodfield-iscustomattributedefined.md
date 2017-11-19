---
title: "IDebugMethodField::IsCustomAttributeDefined |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords: IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bf6d2dbc915638005f377826c5504b2f6bdf859
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
判斷是否已定義特定的自訂屬性。  
  
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
 傳回 S_OK 如果自訂屬性定義於這個方法，否則會傳回 S_FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)