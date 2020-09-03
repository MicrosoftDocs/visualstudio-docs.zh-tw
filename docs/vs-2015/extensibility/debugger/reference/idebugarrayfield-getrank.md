---
title: IDebugArrayField：： GetRank |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198737"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得陣列的順位或維度數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwRank`  
 擴展傳回排名。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 陣列的順位會對應至維度的數目。 在 c + + 和 c # 中，多維陣列其實是陣列的陣列，因此可以只被視為一維陣列 (而且 `GetRank` 方法一律會傳回 1) 。 另一方面，在中， [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 多維度陣列的處理方式不同，因此這類陣列的次序會反映 (的維度數目，而 `GetRank` 方法一律會傳回) 的維度數目。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
