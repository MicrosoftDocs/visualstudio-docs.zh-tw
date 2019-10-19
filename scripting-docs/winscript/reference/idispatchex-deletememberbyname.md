---
title: IDispatchEx：:D eleteMemberByName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576616"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
依名稱刪除成員。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>參數  
 `bstrName`  
 要刪除的成員名稱。  
  
 `grfdex`  
 判斷成員名稱是否區分大小寫。 這可以是下列其中一個值：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|要求以區分大小寫的方式來執行名稱查閱。 不支援區分大小寫查閱的物件可以忽略。|  
|fdexNameCaseInsensitive|要求以不區分大小寫的方式來執行名稱查閱。 不支援不區分大小寫查閱的物件可以忽略。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## <a name="remarks"></a>備註  
 如果刪除成員，DISPID 必須保持有效以進行 `GetNextDispID`。  
  
 如果刪除具有指定名稱的成員，並在稍後重新建立具有相同名稱的成員，則 DISPID 應相同。 （只有大小寫不同的成員是否為「相同」，與物件相依）。  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)