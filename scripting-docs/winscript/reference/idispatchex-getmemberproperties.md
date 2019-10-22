---
title: IDispatchEx：： GetMemberProperties |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574090"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
捕獲成員的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 辨識成員。 使用 `GetDispID` 或 `GetNextDispID` 來取得分派識別碼。  
  
 `grfdexFetch`  
 決定要取得的屬性。 這可以是 `pgrfdex` 和/或下列值組合下所列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|grfdexPropCanAll|結合 fdexPropCanGet、fdexPropCanPut、fdexPropCanPutRef、fdexPropCanCall、fdexPropCanConstruct 和 fdexPropCanSourceEvents。|  
|grfdexPropCannotAll|結合 fdexPropCannotGet、fdexPropCannotPut、fdexPropCannotPutRef、fdexPropCannotCall、fdexPropCannotConstruct 和 fdexPropCannotSourceEvents。|  
|grfdexPropExtraAll|結合 fdexPropNoSideEffects 和 fdexPropDynamicType。|  
|grfdexPropAll|結合 grfdexPropCanAll、grfdexPropCannotAll 和 grfdexPropExtraAll。|  
  
 `pgrfdex`  
 接收要求屬性的 `DWORD` 位址。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexPropCanGet|您可以使用 DISPATCH_PROPERTYGET 來取得成員。|  
|fdexPropCannotGet|無法使用 DISPATCH_PROPERTYGET 取得成員。|  
|fdexPropCanPut|您可以使用 DISPATCH_PROPERTYPUT 來設定成員。|  
|fdexPropCannotPut|無法使用 DISPATCH_PROPERTYPUT 來設定成員。|  
|fdexPropCanPutRef|您可以使用 DISPATCH_PROPERTYPUTREF 來設定成員。|  
|fdexPropCannotPutRef|無法使用 DISPATCH_PROPERTYPUTREF 來設定成員。|  
|fdexPropNoSideEffects|成員沒有任何副作用。 例如，偵錯工具可以安全地取得/設定/呼叫這個成員，而不需要變更正在進行調試的腳本狀態。|  
|fdexPropDynamicType|成員是動態的，而且可以在物件的存留期間變更。|  
|fdexPropCanCall|您可以使用 DISPATCH_METHOD，將成員當做方法來呼叫。|  
|fdexPropCannotCall|無法使用 DISPATCH_METHOD 將成員當做方法來呼叫。|  
|fdexPropCanConstruct|您可以使用 DISPATCH_CONSTRUCT，將成員當做「函式」呼叫。|  
|fdexPropCannotConstruct|無法使用 DISPATCH_CONSTRUCT 將成員當做「函式」呼叫。|  
|fdexPropCanSourceEvents|成員可以引發事件。|  
|fdexPropCannotSourceEvents|成員無法引發事件。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|未知的名稱。|  
  
## <a name="example"></a>範例  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx：： GetDispID](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)