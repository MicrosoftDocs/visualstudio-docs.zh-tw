---
title: IDebugBinder3::FindAlias |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18143522741abb1aebf0569db6ab1387ccd1fc02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722873"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會找出的指定名稱的別名。 在程式中，這將會搜尋所有的別名。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcstrName`  
 [in]若要尋找別名名稱。  
  
 `ppAlias`  
 [out]所表示的別名 （如果有的話） 找到[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`（如果找不到別名） 或錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會初始化為 null，然後再呼叫; 的目的地物件然後它會測試之後，來判斷已找到別名為 null 值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

