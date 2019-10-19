---
title: IDispatchEx：:D eleteMemberByDispID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ead33fb51caff1103ca9abe6bc01f3e0aa6aa3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576643"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
依 DISPID 刪除成員。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 成員識別碼。 使用 `GetDispID` 或 `GetNextDispID` 來取得分派識別碼。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## <a name="remarks"></a>備註  
 如果刪除成員，DISPID 必須保持有效以進行 `GetNextDispID`。  
  
 如果刪除具有指定名稱的成員，並在稍後重新建立具有相同名稱的成員，則 DISPID 應相同。 （只有大小寫不同的成員名稱是否為「相同」，與物件相依）。  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx：： GetDispID](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)