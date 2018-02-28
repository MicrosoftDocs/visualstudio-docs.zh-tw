---
title: "IDispatchEx::GetDispID |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
單一成員名稱對應到其對應的 DISPID，則可在後續呼叫`IDispatchEx::InvokeEx`。  
  
## <a name="syntax"></a>語法  
  
```  
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
 判斷取得成員識別碼的選項。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|區分大小寫的方式進行名稱查閱的要求。 可能不支援區分大小寫對應的物件會被忽略。|  
|fdexNameEnsure|要求的成員不存在時，才能建立。 應該使用的值建立新成員`VT_EMPTY`。|  
|fdexNameImplicit|指出，未明確指定基底物件時，呼叫者正在搜尋的特定名稱的成員物件。|  
|fdexNameCaseInsensitive|不區分大小寫的方式進行名稱查閱的要求。 可能不支援不區分大小寫對應的物件會被忽略。|  
  
 `pid`  
 呼叫端配置的位置來接收 DISPID 結果指標。 如果發生錯誤，`pid`包含 DISPID_UNKNOWN。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`DISP_E_UNKNOWNNAME`|不知道名稱。|  
  
## <a name="remarks"></a>備註  
 `GetDispID`可以使用而不是`GetIDsOfNames`DISPID 取得指定的成員。  
  
 因為`IDispatchEx`可讓您新增和刪除成員的 Dispid 集無法維持不常數物件的存留期間。  
  
 未使用`riid`中的參數`IDispatch::GetIDsOfNames`已移除。  
  
## <a name="example"></a>範例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)