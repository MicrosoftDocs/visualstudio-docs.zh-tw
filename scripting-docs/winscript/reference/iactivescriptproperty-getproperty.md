---
title: IActiveScriptProperty::GetProperty |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726048"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
取得參數所指定的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetProperty(  
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
 要取得之屬性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 屬性的值。  
  
 允許值`dwProperty`下表所述。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|會強制將整數模式，而不是浮動點模式中的指令碼引擎。|  
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
 主機可以使用 SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION 屬性，來通知其他指令碼引擎存在參與為全域物件的指令碼引擎。 例如，Internet Explorer 可以通知[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]僅包含所呈現頁面的引擎[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼。 因此，只有[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎可以將新屬性加入至全域物件的視窗，並沒有要執行相同的 Visual Basic Scripting Edition (VBScript) 引擎。 引擎可以忽略此旗標，或可以使用它來最佳化的新成員加入至全域物件管理。  
  
 主機可以選擇的語言功能集使用 SCRIPTPROP_INVOKEVERSIONING 屬性時，支援[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎已啟動。 如果這個屬性設為 1 (SCRIPTLANGUAGEVERSION_5_7)，可用的語言功能都一樣出現在新版 5.7[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指令碼引擎。 如果它設定為 2 (SCRIPTLANGUAGEVERSION_5_8)，可用的語言功能則是出現在 5.7 版以及 5.8 版本中所加入的功能。 根據預設，這個屬性會設定為 0 (SCRIPTLANGUAGEVERSION_DEFAULT)，除非主機支援不同的預設行為，這是相當於出現在 5.7，版的語言功能集。 比方說，Internet Explorer 8 opts 到[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]5.8 版本所支援的語言功能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Internet Explorer 8 的文件模式是 「 Internet Explorer 8 標準 」 模式時，預設的指令碼引擎。  
  
## <a name="see-also"></a>另請參閱  
 [定義文件相容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本資訊](../../javascript/reference/javascript-version-information.md)