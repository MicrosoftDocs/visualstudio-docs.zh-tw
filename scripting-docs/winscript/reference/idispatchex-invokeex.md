---
title: IDispatchEx::InvokeEx |Microsoft Docs
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
ms.openlocfilehash: e631ecca1181a25fa3cf419f5fc96666f0db3cd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086524"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
提供屬性和方法所公開的存取`IDispatchEx`物件。  
  
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
 辨識成員。 會使用`GetDispID`或`GetNextDispID`取得的分派識別項。  
  
 `lcid`  
 地區設定內容，用於解譯引數。 `lcid`傳遞至`InvokeEx`允許解譯其地區設定特定的引數的物件。  
  
 `wFlags`  
 合法值`wFlags`是：  
  
 DISPATCH_PROPERTYGET &AMP;#124; ，則為 DISPATCH_METHOD &AMP;#124; DISPATCH_PROPERTYPUT &AMP;#124; DISPATCH_PROPERTYPUTREF &AMP;#124; DISPATCH_CONSTRUCT  
  
 描述內容的旗標`InvokeEx`呼叫：  
  
|值|意義|  
|-----------|-------------|  
|DISPATCH_METHOD|方法會叫用成員。 如果屬性具有相同的名稱，可能會設定這個旗標和 DISPATCH_PROPERTYGET 旗標 (藉由定義`IDispatch`)。|  
|DISPATCH_PROPERTYGET|成員會擷取為屬性或資料成員 (藉由定義`IDispatch`)。|  
|DISPATCH_PROPERTYPUT|成員已變更屬性或資料成員 (藉由定義`IDispatch`)。|  
|DISPATCH_PROPERTYPUTREF|變更成員時會參考指派，而不是值的指派。 這個旗標無效，屬性會接受物件的參考時，才 (藉由定義`IDispatch`)。|  
|DISPATCH_CONSTRUCT|成員被當做建構函式。 (這是新的值所定義`IDispatchEx`)。 合法值`wFlags`是：<br /><br /> DISPATCH_PROPERTYGET，則為 DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 結構的指標，此結構包含引數陣列、指名引數之 DISPID 引數的陣列，以及陣列中項目數目的計數。 請參閱`IDispatch`DISPPARAMS 結構的完整描述的文件。  
  
 `pVarRes`  
 結果是預存的則為 Null，如果呼叫端不預期結果的所在的位置指標。 如果指定 DISPATCH_PROPERTYPUT 或 DISPATCH_PROPERTYPUTREF，會忽略這個引數。  
  
 `pei`  
 包含例外狀況資訊的結構指標。 如果應填入這個結構`DISP_E_EXCEPTION`會傳回。 可以是 Null。 請參閱`IDispatch`文件的完整描述`EXCEPINFO`結構。  
  
 `pspCaller`  
 呼叫者，可讓從呼叫者取得服務物件所提供的服務提供者物件的指標。 可以是 Null。  
  
 `IDispatchEx::InvokeEx` 提供所有功能與相同`IDispatch::Invoke`並新增一些擴充功能：  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|表示為建構函式使用的項目。|  
|`pspCaller`|`pspCaller`可讓呼叫端提供的服務物件的存取。 特定的服務可能由呼叫端本身或委派給進一步呼叫端呼叫鏈結。 例如，如果指令碼引擎內的瀏覽器提出`InvokeEx`至外部物件，該物件的呼叫可以依照`pspCaller`從瀏覽器的指令碼引擎取得服務的鏈結。 (請注意，在呼叫鏈結建立鏈結相同，也稱為容器鏈結或站台的鏈結。 建立鏈結可透過其他機制這類`IObjectWithSite`。)|  
|`this` 指標|當設定，則為 DISPATCH_METHOD `wFlags`，可能會有"this"值 「 具名的參數 」。 DISPID 會 DISPID_THIS，而且它必須是第一個具名的參數。|  
  
 未使用`riid`中的參數`IDispatch::Invoke`已移除。  
  
 `puArgArr`中的參數`IDispatch::Invoke`已移除。  
  
 請參閱`IDispatch::Invoke`下列範例中的文件：  
  
 「 呼叫不含引數的方法 」  
  
 「 取得和設定屬性 」  
  
 [傳送參數]  
  
 [索引的屬性]  
  
 「 叫用期間引發例外狀況 」  
  
 「 傳回的錯誤 」  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP_E_BADPARAMCOUNT|提供給 DISPPARAMS 項目數與不同的方法或屬性所接受的引數數目。|  
|DISP_E_BADVARTYPE|中的引數的其中一個`rgvarg`不是有效的 variant 類型。|  
|DISP_E_EXCEPTION|應用程式必須引發例外狀況。 在此情況下，結構會傳入`pei`應該會自動填入。|  
|DISP_E_MEMBERNOTFOUND|要求的成員不存在，或呼叫`InvokeEx`嘗試設定唯讀屬性的值。|  
|DISP_E_NONAMEDARGS|這個實作`IDispatch`不支援具名引數。|  
|DISP_E_OVERFLOW|中的引數的其中一個`rgvarg`不強制轉型為指定的型別。|  
|DISP_E_PARAMNOTFOUND|其中一個參數 Dispid 並未對應至參數的方法。|  
|DISP_E_TYPEMISMATCH|一或多個引數可能不會強制轉型。|  
|DISP_E_UNKNOWNLCID|叫用的成員會解譯字串引數，根據 LCID、 LCID 不能辨識。 如果不需要的 LCID 解譯引數，應該不會傳回此錯誤。|  
|DISP_E_PARAMNOTOPTIONAL|已省略必要的參數。|  
  
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
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)