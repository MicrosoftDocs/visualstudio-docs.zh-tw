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
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576608"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
將單一成員名稱對應到其對應的 DISPID，然後再用於 `IDispatchEx::InvokeEx` 的後續呼叫。  
  
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
|fdexNameEnsure|要求建立成員（如果尚未存在的話）。 應該使用值 `VT_EMPTY` 來建立新成員。|  
|fdexNameImplicit|指出當基底物件未明確指定時，呼叫者正在搜尋特定名稱成員的物件。|  
|fdexNameCaseInsensitive|要求以不區分大小寫的方式來執行名稱查閱。 不支援不區分大小寫查閱的物件可能會略過。|  
  
 `pid`  
 呼叫端配置的位置指標，用來接收 DISPID 結果。 如果發生錯誤，`pid` 包含 DISPID_UNKNOWN。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`DISP_E_UNKNOWNNAME`|未知的名稱。|  
  
## <a name="remarks"></a>備註  
 `GetDispID` 可以用來取代 `GetIDsOfNames`，以取得指定成員的 DISPID。  
  
 因為 `IDispatchEx` 允許新增和刪除成員，所以 Dispid 的集合在物件的存留期內不會保持不變。  
  
 @No__t_1 中未使用的 `riid` 參數已移除。  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)