---
title: "IDispatchEx::GetMemberProperties |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
擷取成員的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 辨識成員。 使用`GetDispID`或`GetNextDispID`取得的分派識別項。  
  
 `grfdexFetch`  
 決定要擷取的屬性。 這可以是底下所列的值的組合`pgrfdex`和 （或) 下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|grfdexPropCanAll|結合 fdexPropCanGet、 fdexPropCanPut、 fdexPropCanPutRef、 fdexPropCanCall、 fdexPropCanConstruct 和 fdexPropCanSourceEvents。|  
|grfdexPropCannotAll|結合 fdexPropCannotGet、 fdexPropCannotPut、 fdexPropCannotPutRef、 fdexPropCannotCall、 fdexPropCannotConstruct 和 fdexPropCannotSourceEvents。|  
|grfdexPropExtraAll|結合 fdexPropNoSideEffects 和 fdexPropDynamicType。|  
|grfdexPropAll|結合了 grfdexPropCanAll、 grfdexPropCannotAll 和 grfdexPropExtraAll。|  
  
 `pgrfdex`  
 位址`DWORD`接收要求的內容。 這可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|fdexPropCanGet|您可以使用 DISPATCH_PROPERTYGET 取得之成員。|  
|fdexPropCannotGet|無法使用 DISPATCH_PROPERTYGET 取得之成員。|  
|fdexPropCanPut|成員可以使用 DISPATCH_PROPERTYPUT 來設定。|  
|fdexPropCannotPut|成員不能使用 DISPATCH_PROPERTYPUT 設定。|  
|fdexPropCanPutRef|成員可以使用 DISPATCH_PROPERTYPUTREF 來設定。|  
|fdexPropCannotPutRef|成員不能使用 DISPATCH_PROPERTYPUTREF 設定。|  
|fdexPropNoSideEffects|成員並沒有任何副作用。 例如，偵錯工具可以安全地取得/設定/呼叫此成員，而不需要變更指令碼進行偵錯的狀態。|  
|fdexPropDynamicType|成員是動態的且可以變更物件的存留期間。|  
|fdexPropCanCall|可以為使用 DISPATCH_METHOD 方法呼叫成員。|  
|fdexPropCannotCall|無法為使用 DISPATCH_METHOD 方法呼叫成員。|  
|fdexPropCanConstruct|成員可以使用 DISPATCH_CONSTRUCT 是建構函式呼叫。|  
|fdexPropCannotConstruct|成員不能使用 DISPATCH_CONSTRUCT 是建構函式呼叫。|  
|fdexPropCanSourceEvents|成員可以引發事件。|  
|fdexPropCannotSourceEvents|成員無法引發事件。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|不知道名稱。|  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)