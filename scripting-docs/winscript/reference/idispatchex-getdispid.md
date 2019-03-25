---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95ab1d72e5b2f608c51ac6e56be1986df8945ec2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152859"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
單一成員名稱對應到其對應的 DISPID，然後在後續呼叫使用`IDispatchEx::InvokeEx`。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bstrName`  
 傳入要對應的名稱。  
  
 `grfdex`  
 決定的選項，以取得成員的識別碼。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|名稱查閱會區分大小寫的方式完成的要求。 可能會忽略不支援區分大小寫的查閱的物件。|  
|fdexNameEnsure|要求不存在時，就會建立的成員。 應該使用的值建立新的成員`VT_EMPTY`。|  
|fdexNameImplicit|表示呼叫端未明確指定基底物件時，，正在搜尋物件的特定名稱的成員。|  
|fdexNameCaseInsensitive|名稱查閱不區分大小寫的方式完成的要求。 可能會忽略不支援不區分大小寫的查閱的物件。|  
  
 `pid`  
 呼叫端配置的位置，來接收 DISPID 結果的指標。 如果發生錯誤，`pid`包含 DISPID_UNKNOWN。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`DISP_E_UNKNOWNNAME`|不知道名稱。|  
  
## <a name="remarks"></a>備註  
 `GetDispID` 可以使用而不是`GetIDsOfNames`取得指定之成員的 DISPID。  
  
 因為`IDispatchEx`可讓您新增和刪除成員的 Dispid 集不會不保持不變的物件存留期。  
  
 未使用`riid`中的參數`IDispatch::GetIDsOfNames`已移除。  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)