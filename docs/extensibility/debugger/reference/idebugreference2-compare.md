---
title: IDebugReference2::Compare |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ede48e5236887e3d8fdb22425d92c8514636f94
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
比較到另一個參考。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCompare`  
 [in]中的值[REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)指定的比較運算，例如，等於、 小於或大於的列舉。  
  
 `pReference`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，代表要比較的參考。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)