---
title: IActiveScriptProperty：： SetProperty |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571316"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
設定參數所指定的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwProperty`  
 要設定的屬性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 屬性的值。  
  
 下表將說明 `dwProperty` 所允許的值。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|強制腳本引擎以整數模式分割，而不是浮點模式。 預設值是 `False`。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|允許取代腳本引擎的字串比較功能。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|通知腳本引擎，不存在任何其他腳本引擎來參與全域物件。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|強制 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎選取一組要支援的語言功能。 @No__t_0 腳本引擎所支援的預設語言功能集，相當於 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎5.7 版中出現的語言功能集。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 若要啟用或停用整數除法，請叫用 `SetProperty`，並將 `Boolean` 轉換成 `Object`。 根據預設，屬性值為 `False`。 如果您將它設定為 `True`，除法運算就只會傳回整數。  
  
 若要啟用或停用自訂字串比較，請叫用 `SetProperty` 並傳入 `Object` 值。 您傳入的物件必須執行介面[IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)。 每次執行字串比較函數時，都會呼叫[IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)介面的[StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md)方法。  
  
 若要選取 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎初始化時所要支援的一組語言功能，請叫用 `SetProperty` 並傳遞對應至要啟用 SCRIPTPROP_INVOKEVERSIONING 之語言功能集的值。 如果這個屬性設定為1（SCRIPTLANGUAGEVERSION_5_7），可用的語言功能就會與5.7 版 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎中所顯示的相同。 如果設定為2（SCRIPTLANGUAGEVERSION_5_8），可用的語言功能就是在版本5.7 中所顯示的新功能，以及5.8 版中新增的功能。 根據預設，這個屬性會設定為0（SCRIPTLANGUAGEVERSION_DEFAULT），這相當於出現在5.7 版中的語言功能集，除非該主機支援不同的預設行為。 例如，當 Internet Explorer 8 的預設檔案模式為「Internet Explorer 8 標準」模式時，Internet Explorer 8 會加入宣告5.8 版所支援的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 語言功能 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎。 將 Internet Explorer 8 檔案模式切換到 Internet Explorer 7 標準或「可執行模式」，會重設 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的腳本引擎，僅支援5.7 版 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎中存在的語言功能集。  
  
> [!NOTE]
> 只有在初始化 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎時，才應設定 SCRIPTPROP_INVOKEVERSIONING。  
  
## <a name="example"></a>範例  
 下列範例示範如何強制腳本引擎使用整數除法，以及如何允許比較函數的多載。  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>請參閱  
 [定義檔相容性](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)    
 [版本資訊](../../javascript/reference/javascript-version-information.md)