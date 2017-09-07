---
title: "IDebugArrayObject::GetElement |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f1d56b32b91b840cc87bb3ba50107b65c54c79d5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
取得陣列的項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)表示項目的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將所有項目的陣列物件視為一維陣列，即使多維陣列物件。 例如，假設陣列`myarray[3][2][6]`和`dwIndex`20 的參數，這個方法會傳回的項目`myarray[1][1][2]`，和`dwIndex`21 參數會傳回的項目`myarray[1][1][3]`。 使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)方法，以判斷陣列中的項目總數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
