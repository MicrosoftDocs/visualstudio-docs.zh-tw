---
title: IEnumDebugCustomAttributes::Clone |Microsoft Docs
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
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9819d36fd2817bc7c15d6e607790c3dd3788f1af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797130"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立列舉值，包含目前的列舉值相同的列舉型別狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Clone (   
   IEnumCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppEnum  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

