---
title: IDebugReference2::Compare |Microsoft Docs
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
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8f61526ac65c947af47bf278029f9f80d72b9a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491363"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugReference2::Compare](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-compare)。  
  
比較到另一個參考。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]值，以從[REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)列舉，指定的比較作業，例如，等於、 小於或大於。  
  
 `pReference`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示要比較的參考。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)

