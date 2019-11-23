---
title: IActiveScriptProperty：： GetProperty |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571409"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
取得參數所指定的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
 要取得的屬性值。  
  
 `pvarIndex`  
 未使用。  
  
 `pvarValue`  
 屬性的值。  
  
 下表將說明 `dwProperty` 所允許的值。  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|強制腳本引擎以整數模式分割，而不是浮點模式。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|允許取代腳本引擎的字串比較功能。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|通知腳本引擎，不存在任何其他腳本引擎來參與全域物件。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|強制 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎選取一組要支援的語言功能。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎所支援的預設語言功能集，相當於 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎5.7 版中出現的語言功能集。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 主機可以使用 [SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION] 屬性來通知腳本引擎，讓全域物件無法參與其他腳本引擎。 例如，Internet Explorer 可以通知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎呈現的頁面只包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本。 因此，只有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎可以將新的屬性加入至全域物件視窗，而且沒有任何 Visual Basic Scripting Edition （VBScript）引擎可以執行相同的動作。 引擎可以忽略此旗標，也可以使用它來優化新增至全域物件之新成員的管理。  
  
 主機可以使用 [SCRIPTPROP_INVOKEVERSIONING] 屬性，選取 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎啟動時所要支援的一組語言功能。 如果這個屬性設定為1（SCRIPTLANGUAGEVERSION_5_7），可用的語言功能就會與 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎的5.7 版中所顯示的相同。 如果設定為2（SCRIPTLANGUAGEVERSION_5_8），可用的語言功能就是在版本5.7 中出現的功能，以及5.8 版中新增的功能。 根據預設，這個屬性會設定為0（SCRIPTLANGUAGEVERSION_DEFAULT），這相當於出現在5.7 版中的語言功能集，除非該主機支援不同的預設行為。 比方說，當 Internet Explorer 8 的檔案模式為「Internet Explorer 8 標準」模式時，Internet Explorer 8 預設會納入5.8 版所支援的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 語言功能 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 腳本引擎。  
  
## <a name="see-also"></a>另請參閱  
 [定義檔相容性](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本資訊](../../javascript/reference/javascript-version-information.md)