---
title: "IDebugArrayField::GetRank |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 786f765e684f720c8c29b91331259e772bd5a007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
取得的順位或陣列的維度數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]傳回次序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 陣列陣序對應至維度的數目。 C + + 和 C# 中，多維度陣列其實是陣列的陣列，因此可以視為只是一維陣列 (和`GetRank`方法一律會傳回 1)。 在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]相反地，多維度陣列的處理方式不同，這類陣列的陣序反映的維度數目 (和`GetRank`方法永遠都會傳回的維度數目)。  
  
## <a name="see-also"></a>請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)