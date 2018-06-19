---
title: IDispError::GetSource |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 922f95206d341773632b84c3922ea3b240d8d1ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727968"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
傳回對類別或引發錯誤的應用程式的語言相依程式設計識別項。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrSource`  
 [out]字串，包含在表單中的程式設計識別項`progname.objectname`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法用來決定類別或應用程式發生例外狀況。 程式設計識別項可能會傳回在指定的引動過程時提供的地區設定識別碼 (LCID) 的語言。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)