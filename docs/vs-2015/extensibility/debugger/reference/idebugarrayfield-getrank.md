---
title: IDebugArrayField::GetRank |Microsoft Docs
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
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1f06df292c5ed9ed2b7201589f5aa659b3f9716
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177277"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得的順位或陣列的維度數目。  
  
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
 [out]傳回順位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 陣列陣序對應至維度的數目。 C + + 和 C# 中，多維度陣列其實是陣列的陣列，因此可被視為只是一維陣列 (和`GetRank`方法一律會傳回 1)。 在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]相反地，多維度陣列的處理方式不同，這類陣列的陣序反映的維度數目 (和`GetRank`方法一律會傳回的維度數目)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)

