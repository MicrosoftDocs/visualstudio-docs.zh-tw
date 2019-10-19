---
title: IScriptEntry：： GetSignature |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575424"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
傳回 `IScriptEntry` 函式物件的類型資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppti`  
 脫銷與這個 `IScriptEntry` 函式物件相關聯的類型資訊。  
  
 `piMethod`  
 脫銷@No__t_0 物件中的方法索引。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 您可以使用[IScriptEntry：： SetSignature](../../winscript/reference/iscriptentry-setsignature.md)或[IScriptNode：： CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)來設定型別資訊。 型別資訊也可以根據內部函式標記法來產生。  
  
## <a name="see-also"></a>請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)