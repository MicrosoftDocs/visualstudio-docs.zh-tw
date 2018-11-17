---
title: IDebugObject::GetValue |Microsoft Docs
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
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c43487960fdca21e4c716514a3533db90c6ae76
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770266"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得物件的值做為一系列連續的位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pValue`  
 [in、 out]陣列，其中會填入一連串連續的位元組表示之物件的值。  
  
 `nSize`  
 [in]要擷取的位元組數目上限。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 取得的值可以藉由呼叫擷取的位元組總數[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

