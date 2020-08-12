---
title: IDispatchEx：： GetDispID |Microsoft Docs
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
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144529"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
將單一成員名稱對應至其相對應的 DISPID，然後再用於後續呼叫 `IDispatchEx::InvokeEx` 。  
  
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
 決定取得成員識別碼的選項。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexNameCaseSensitive|要求以區分大小寫的方式來執行名稱查閱。 不支援區分大小寫查閱的物件可能會略過。|  
|fdexNameEnsure|要求建立成員（如果尚未存在的話）。 應該使用值來建立新成員 `VT_EMPTY` 。|  
|fdexNameImplicit|指出當未明確指定基底物件時，呼叫者會搜尋特定名稱成員的物件 (s) 。|  
|fdexNameCaseInsensitive|要求以不區分大小寫的方式來執行名稱查閱。 不支援不區分大小寫查閱的物件可能會略過。|  
  
 `pid`  
 呼叫端配置的位置指標，用來接收 DISPID 結果。 如果發生錯誤，會 `pid` 包含 DISPID_UNKNOWN。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一值：  
  
|值|意義|
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`DISP_E_UNKNOWNNAME`|未知的名稱。|  
  
## <a name="remarks"></a>備註  
 `GetDispID`可以用 `GetIDsOfNames` 來取代，以取得指定成員的 DISPID。  
  
 因為 `IDispatchEx` 允許新增和刪除成員，所以 dispid 集在物件的存留期內不會保持不變。  
  
 中未使用的 `riid` 參數已 `IDispatch::GetIDsOfNames` 被移除。  
  
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