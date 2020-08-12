---
title: IDispatchEx：： InvokeEx |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 673b3f1e64caa79dc2b21641209423d93fe0f834
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144411"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
提供物件所公開之屬性和方法的存取權 `IDispatchEx` 。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 辨識成員。 使用 `GetDispID` 或 `GetNextDispID` 來取得分派識別碼。  
  
 `lcid`  
 地區設定內容，用於解譯引數。 `lcid`會傳遞至 `InvokeEx` ，以允許物件解讀其地區設定特定的引數。  
  
 `wFlags`  
 的合法值為 `wFlags` ：  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 描述呼叫內容的旗標 `InvokeEx` ：  
  
|值|意義|  
|-----------|-------------|  
|DISPATCH_METHOD|會叫用成員做為方法。 如果屬性具有相同的名稱，則可以將這個和 DISPATCH_PROPERTYGET 旗標設定 (`IDispatch`) 定義。|  
|DISPATCH_PROPERTYGET|此成員會以屬性或資料成員的形式抓取 (由 `IDispatch`) 所定義。|  
|DISPATCH_PROPERTYPUT|成員會變更為屬性或資料成員 (由) 所定義 `IDispatch` 。|  
|DISPATCH_PROPERTYPUTREF|成員是由參考指派來變更，而不是值指派。 只有當屬性接受) 所定義 (物件的參考時，此旗標才有效 `IDispatch` 。|  
|DISPATCH_CONSTRUCT|成員正當做函式使用。  (這是由) 定義的新值 `IDispatchEx` 。 的合法值為 `wFlags` ：<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 結構的指標，此結構包含引數陣列、指名引數之 DISPID 引數的陣列，以及陣列中項目數目的計數。 如需 `IDispatch` DISPPARAMS 結構的完整描述，請參閱檔。  
  
 `pVarRes`  
 要儲存結果之位置的指標，如果呼叫端不預期結果，則為 Null。 如果指定 DISPATCH_PROPERTYPUT 或 DISPATCH_PROPERTYPUTREF，則會忽略這個引數。  
  
 `pei`  
 包含例外狀況資訊的結構指標。 如果傳回，則應該填入此結構 `DISP_E_EXCEPTION` 。 可以是 Null。 如需 `IDispatch` 結構的完整描述，請參閱檔 `EXCEPINFO` 。  
  
 `pspCaller`  
 呼叫端提供的服務提供者物件指標，可讓物件從呼叫端取得服務。 可以是 Null。  
  
 `IDispatchEx::InvokeEx`提供與相同的所有功能 `IDispatch::Invoke` ，並新增一些延伸模組：  
  
|值|意義|
|-|-|  
|DISPATCH_CONSTRUCT|表示此專案正當做函式使用。|  
|`pspCaller`|`pspCaller`允許物件存取呼叫者所提供的服務。 特定的服務可能由呼叫端本身處理，或委派給呼叫端的其他呼叫端。 例如，如果瀏覽器內的腳本引擎 `InvokeEx` 呼叫外部物件，物件可以遵循該 `pspCaller` 鏈，從腳本引擎或瀏覽器取得服務。  (請注意，呼叫鏈與建立鏈（也稱為容器鏈或網站鏈）不同。 建立鏈可能可以透過一些其他機制（例如）來使用 `IObjectWithSite` 。 ) |  
|`this` 指標|當 DISPATCH_METHOD 在中設定時 `wFlags` ，可能會有 "this" 值的「已具名引數」。 DISPID 將會 DISPID_THIS，而且必須是第一個名為的參數。|  
  
 中未使用的 `riid` 參數已 `IDispatch::Invoke` 被移除。  
  
 `puArgArr`中的參數已 `IDispatch::Invoke` 移除。  
  
 請參閱 `IDispatch::Invoke` 下列範例的檔：  
  
 「呼叫沒有引數的方法」  
  
 「取得和設定屬性」  
  
 「傳遞參數」  
  
 「索引屬性」  
  
 「叫用期間引發例外狀況」  
  
 「傳回錯誤」  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一值：  
  
|值|意義|  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|提供給 DISPPARAMS 的元素數目與方法或屬性所接受的引數數目不同。|  
|DISP_E_BADVARTYPE|中的其中一個引數 `rgvarg` 不是有效的 variant 類型。|  
|DISP_E_EXCEPTION|應用程式必須引發例外狀況。 在此情況下，應該填入傳入的結構 `pei` 。|  
|DISP_E_MEMBERNOTFOUND|要求的成員不存在，或呼叫嘗試 `InvokeEx` 設定唯讀屬性的值。|  
|DISP_E_NONAMEDARGS|這個的執行不 `IDispatch` 支援具名引數。|  
|DISP_E_OVERFLOW|中的其中一個引數無法 `rgvarg` 強制轉型為指定的類型。|  
|DISP_E_PARAMNOTFOUND|其中一個參數 Dispid 不會對應到方法上的參數。|  
|DISP_E_TYPEMISMATCH|無法強制轉型一或多個引數。|  
|DISP_E_UNKNOWNLCID|所叫用的成員會根據 LCID 來解讀字串引數，而且無法辨識 LCID。 如果不需要 LCID 來解讀引數，則不應傳回此錯誤。|  
|DISP_E_PARAMNOTOPTIONAL|省略了必要的參數。|  
  
## <a name="example"></a>範例  
  
```cpp
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
 [IDispatchEx：： GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)