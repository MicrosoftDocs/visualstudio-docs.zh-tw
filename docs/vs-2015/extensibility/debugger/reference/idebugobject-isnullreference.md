---
title: IDebugObject::IsNullReference |Microsoft Docs
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
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 580ea2db9a9b9e7d3e40aff7f1d705a37a090513
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845157"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

測試這個物件是否為 null 參考。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfIsNull`  
 [out]會傳回非零 (`TRUE`) 如果此物件為 null 的參考; 否則會傳回零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 Null 的參考表示空的物件或尚未指派給物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

