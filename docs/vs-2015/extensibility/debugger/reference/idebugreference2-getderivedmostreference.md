---
title: IDebugReference2::GetDerivedMostReference |Microsoft Docs
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
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b680571bc2edc54e89b1625b012e5a34885ffe9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491961"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugReference2::GetDerivedMostReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-getderivedmostreference)。  
  
取得參考的最具衍生性參考。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDerivedMost`  
 [out]傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示最具衍生性的屬性。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
 例如，如果這個屬性會描述該物件會實作`ClassRoot`這是實際的具現化，但`ClassDerived`衍生自`ClassRoot`，則這個方法會傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件代表參考`ClassDerived`物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

