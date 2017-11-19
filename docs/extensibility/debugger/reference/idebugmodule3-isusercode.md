---
title: "IDebugModule3::IsUserCode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::IsUserCode
helpviewer_keywords: IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dcade316ef9bd58cc7be2906df3ca3cfa9fa33b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
擷取模組是否代表使用者程式碼的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfUser`  
 [out]非零 (`TRUE`) 模組會代表使用者程式碼，如果零 (`FALSE`) 如果不存在。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)