---
title: IDispatchEx::DeleteMemberByName |Microsoft Docs
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000884"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
依名稱刪除的成員。  
  
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
 判斷是否區分大小寫的成員名稱。 這可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|名稱查閱會區分大小寫的方式完成的要求。 您可以忽略不支援區分大小寫的查閱的物件。|  
|fdexNameCaseInsensitive|名稱查閱不區分大小寫的方式完成的要求。 您可以忽略不支援不區分大小寫的查閱的物件。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## <a name="remarks"></a>備註  
 如果刪除的成員時，必須保持有效 DISPID `GetNextDispID`。  
  
 如果已刪除具有指定名稱的成員，而且稍後會重新建立具有相同名稱的成員，DISPID 應該相同。 （只有大小寫不同的成員是否 「 相同 」 是物件相依。）  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)