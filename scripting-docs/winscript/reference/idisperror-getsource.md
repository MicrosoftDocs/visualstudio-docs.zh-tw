---
title: IDispError：： GetSource |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573097"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
針對引發錯誤的類別或應用程式，傳回與語言相關的程式設計識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrSource`  
 脫銷包含程式設計識別碼的字串，格式為 `progname.objectname`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法是用來判斷發生例外狀況的類別或應用程式。 以調用時提供的地區設定識別碼（LCID）所指定的語言，可能會傳回程序設計識別碼。  
  
> [!NOTE]
> 這個方法尚未實作。  
  
## <a name="see-also"></a>請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)