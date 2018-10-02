---
title: IDebugExtendedField::GetExtendedKind |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0646c0edc95b2852fa02787aa01a8312626eec96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499878"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugExtendedField::GetExtendedKind](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugextendedfield-getextendedkind)。  
  
擷取指定的擴充的欄位類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```csharp  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwKind`  
 [in、 out]值從[FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md)定義的欄位類型的列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

