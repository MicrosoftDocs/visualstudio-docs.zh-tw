---
title: IDispatchEx::InvokeEx |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24730078"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
提供公開的屬性和方法的存取`IDispatchEx`物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 辨識成員。 使用`GetDispID`或`GetNextDispID`取得的分派識別項。  
  
 `lcid`  
 地區設定內容，用於解譯引數。 `lcid`傳遞至`InvokeEx`允許要解譯成地區設定特定的引數的物件。  
  
 `wFlags`  
 合法值`wFlags`是：  
  
 DISPATCH_PROPERTYGET &#124;DISPATCH_METHOD &#124;DISPATCH_PROPERTYPUT &#124;DISPATCH_PROPERTYPUTREF &#124;DISPATCH_CONSTRUCT  
  
 描述之內容的旗標`InvokeEx`呼叫：  
  
|值|意義|  
|-----------|-------------|  
|DISPATCH_METHOD|方法會叫用成員。 如果屬性具有相同的名稱，可以設定這和 DISPATCH_PROPERTYGET 旗標 (由`IDispatch`)。|  
|DISPATCH_PROPERTYGET|成員會擷取為屬性或資料成員 (由`IDispatch`)。|  
|DISPATCH_PROPERTYPUT|成員已變更屬性或資料成員 (由`IDispatch`)。|  
|DISPATCH_PROPERTYPUTREF|變更成員時會參考指派，而不是值的指派。 這個旗標無效，屬性會接受物件的參考時，才 (由`IDispatch`)。|  
|DISPATCH_CONSTRUCT|正在使用該成員是建構函式。 (這是所定義的新值`IDispatchEx`)。 合法值`wFlags`是：<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 結構的指標，此結構包含引數陣列、指名引數之 DISPID 引數的陣列，以及陣列中項目數目的計數。 請參閱`IDispatch`DISPPARAMS 結構的完整描述的文件。  
  
 `pVarRes`  
 可以是預存或 Null，如果呼叫端必須確保沒有結果結果之位置的指標。 如果指定了 DISPATCH_PROPERTYPUT 或 DISPATCH_PROPERTYPUTREF，會忽略這個引數。  
  
 `pei`  
 包含例外狀況資訊的結構指標。 如果此結構必須填滿`DISP_E_EXCEPTION`傳回。 可以是 Null。 請參閱`IDispatch`文件的完整說明`EXCEPINFO`結構。  
  
 `pspCaller`  
 呼叫端，可讓物件從呼叫者取得服務所提供的服務提供者物件的指標。 可以是 Null。  
  
 `IDispatchEx::InvokeEx`提供所有與相同的功能`IDispatch::Invoke`並加入一些擴充功能：  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|指出項目做建構函式。|  
|`pspCaller`|`pspCaller`允許呼叫端提供的服務物件存取。 特定服務可能由呼叫端本身或委派給其他呼叫端呼叫鏈結。 例如，如果指令碼引擎內瀏覽器可讓您`InvokeEx`至外部物件，該物件的呼叫可以依照`pspCaller`從指令碼引擎或瀏覽器取得服務的鏈結。 (請注意，呼叫鏈結無法建立鏈結相同，也稱為容器鏈結或站台鏈結。 建立鏈結可透過其他機制例如`IObjectWithSite`。)|  
|`this` 指標|當設定 DISPATCH_METHOD `wFlags`，可能有 「 具名的參數 」 為"this"值。 DISPID 將 DISPID_THIS，它必須是第一個具名的參數。|  
  
 未使用`riid`中的參數`IDispatch::Invoke`已移除。  
  
 `puArgArr`中的參數`IDispatch::Invoke`已移除。  
  
 請參閱`IDispatch::Invoke`文件，如下列範例：  
  
 「 呼叫沒有引數的方法 」  
  
 「 取得和設定屬性"  
  
 「 傳遞參數 」  
  
 [索引的屬性]  
  
 「 叫用期間引發例外狀況 」  
  
 「 傳回的錯誤 」  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|提供給 DISPPARAMS 項目數與不同的方法或屬性接受的引數。|  
|DISP_E_BADVARTYPE|其中一個引數中`rgvarg`不是有效的 variant 類型。|  
|DISP_E_EXCEPTION|應用程式需要引發例外狀況。 在此情況下，結構會傳入`pei`應填入。|  
|DISP_E_MEMBERNOTFOUND|要求的成員不存在，或是呼叫`InvokeEx`嘗試設定唯讀屬性的值。|  
|DISP_E_NONAMEDARGS|這項實作`IDispatch`不支援具名引數。|  
|DISP_E_OVERFLOW|其中一個引數中`rgvarg`不會強制轉成指定的型別。|  
|DISP_E_PARAMNOTFOUND|其中一個參數 Dispid 不對應上之方法的參數。|  
|DISP_E_TYPEMISMATCH|無法套用一或多個引數。|  
|DISP_E_UNKNOWNLCID|所叫用的成員會解譯字串引數，根據 LCID、 LCID 不能辨識。 如果 LCID 不需要用於解譯引數，應不會傳回這個錯誤。|  
|DISP_E_PARAMNOTOPTIONAL|已省略必要的參數。|  
  
## <a name="example"></a>範例  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)