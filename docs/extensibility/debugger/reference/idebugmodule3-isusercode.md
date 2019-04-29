---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39bbef1e8b831473b196d0609459b80a05e5fc2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872753"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取有關模組是否代表使用者程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfUser`  
 [out]非零值 (`TRUE`) 如果模組會代表使用者程式碼，則為零 (`FALSE`) 如果沒有。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
