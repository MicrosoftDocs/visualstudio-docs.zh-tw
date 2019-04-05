---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 44413531cf3a91c6677d9ce3d56e10646307ffd6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940320"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
