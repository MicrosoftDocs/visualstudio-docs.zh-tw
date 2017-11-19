---
title: "IActiveScriptProperty::SetProperty |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
設定參數所指定的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
 允許值`dwProperty`下表所述。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|會強制將整數模式，而不是浮動點模式中的指令碼引擎。 預設值是 `False`。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|可讓指令碼引擎要被取代的字串比較函式。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|通知其他指令碼引擎存在參與為全域物件的指令碼引擎。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|強制[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]來選取一組支援的語言功能的指令碼引擎。 支援的語言功能的預設集[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎就相當於出現在 5.7 版的語言功能集[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 若要啟用或停用整數除法，叫用`SetProperty`和轉換`Boolean`至`Object`。 根據預設，屬性值是`False`。 如果您將它設定為`True`，除法作業會傳回只的整數。  
  
 若要啟用或停用自訂的字串比較，請叫用`SetProperty`並傳入`Object`值。 您要傳入的物件必須實作介面[IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)。 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md)方法[IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)介面會執行字串比較函式每次呼叫。  
  
 若要選取的語言功能，當支援一組[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎初始化，會叫用`SetProperty`，並將對應的值傳遞至設為 SCRIPTPROP_INVOKEVERSIONING 啟用的語言功能。 如果這個屬性設為 1 (SCRIPTLANGUAGEVERSION_5_7)，可用的語言功能都一樣出現在新版 5.7[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎。 如果它設定為 2 (SCRIPTLANGUAGEVERSION_5_8)，可用的語言功能則是出現在 5.7 版除了 5.8 版本中所加入的新功能。 根據預設，這個屬性會設定為 0 (SCRIPTLANGUAGEVERSION_DEFAULT)，除非主機支援不同的預設行為，這是相當於出現在 5.7，版的語言功能集。 例如，Internet Explorer 8 opts 到[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]5.8 的版本所支援的語言功能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Internet Explorer 8 的預設文件模式是 「 Internet Explorer 8 標準 」 模式時，預設的指令碼引擎。 切換至 Internet Explorer 7 標準 Internet Explorer 8 文件模式或 Quirks 模式下重設[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]5.7 版支援只會將語言功能集，存在於指令碼引擎[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎。  
  
> [!NOTE]
>  時，才應該設定 SCRIPTPROP_INVOKEVERSIONING[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎正在初始化。  
  
## <a name="example"></a>範例  
 下列範例示範如何強制使用整數除法指令碼引擎以及如何允許的比較函式多載。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [定義文件相容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本資訊](../../javascript/reference/javascript-version-information.md)