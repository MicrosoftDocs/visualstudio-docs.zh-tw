---
title: IDebugMethodField::GetThis |Microsoft Docs
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
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d942fab313e54497919de03081e7a47aff69ac7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888797"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得`this`(`Me`在[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 的物件，包含方法的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppClass`  
 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，代表"this"指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在物件導向語言中，有通常是目前的具現化之類別的隱含的指標。 這就所謂`this`在 C# / c + + 和 as`Me`在[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

