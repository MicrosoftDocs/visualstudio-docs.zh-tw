---
title: "IDispatchEx::DeleteMemberByName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
依名稱刪除成員。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>參數  
 `bstrName`  
 要刪除的成員名稱。  
  
 `grfdex`  
 決定是否區分大小寫的成員名稱。 這可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|區分大小寫的方式進行名稱查閱的要求。 您可以忽略不支援區分大小寫對應的物件。|  
|fdexNameCaseInsensitive|不區分大小寫的方式進行名稱查閱的要求。 您可以忽略不支援不區分大小寫對應的物件。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## <a name="remarks"></a>備註  
 如果刪除的成員，則必須一直保持有效的 DISPID `GetNextDispID`。  
  
 如果已刪除具有指定名稱的成員之後重新建立具有相同名稱的成員，DISPID 應相同。 （只有大小寫不同的成員是否 「 相同 」 是物件而定）。  
  
## <a name="example"></a>範例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)