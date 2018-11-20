---
title: IDebugArrayObject::GetElement |Microsoft Docs
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
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20da5d4770ecfe36fcb52e3609ee28be38491e84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764991"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得陣列的項目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwIndex`  
 [in]項目索引。  
  
 `ppElement`  
 [out]傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面，表示項目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將所有項目的陣列物件視為一維陣列，即使是多維式陣列物件。 例如，假設陣列`myarray[3][2][6]`並`dwIndex`20 個參數，這個方法會傳回的項目`myarray[1][1][2]`，和`dwIndex`21 參數會傳回的項目`myarray[1][1][3]`。 使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)方法來判斷陣列中的項目總數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

