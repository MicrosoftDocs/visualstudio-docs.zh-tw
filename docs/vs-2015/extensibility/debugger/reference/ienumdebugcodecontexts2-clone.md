---
title: IEnumDebugCodeContexts2::Clone |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugCodeContexts2::Clone
helpviewer_keywords:
- IEnumDebugCodeContexts2::Clone
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c5c873569b9f5c9c3c7750ce630fa9642f2ccaf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487908"
---
# <a name="ienumdebugcodecontexts2clone"></a>IEnumDebugCodeContexts2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IEnumDebugCodeContexts2::Clone](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcodecontexts2-clone)。  
  
傳回一份目前的列舉，為個別的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

