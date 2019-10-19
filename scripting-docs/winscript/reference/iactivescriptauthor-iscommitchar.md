---
title: IActiveScriptAuthor：： IsCommitChar |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.IsCommitChar
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::IsCommitChar
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f442bdc22f569cac6d706d739b2cfb37e07398b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576344"
---
# <a name="iactivescriptauthoriscommitchar"></a>IActiveScriptAuthor::IsCommitChar
傳回值，指出指定的字元是否應觸發應用程式的語句完成認可。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ch`  
 在要測試的字元。  
  
 `pfcommit`  
 [out] `True` 如果字元是認可字元，則為，否則，`False`。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)