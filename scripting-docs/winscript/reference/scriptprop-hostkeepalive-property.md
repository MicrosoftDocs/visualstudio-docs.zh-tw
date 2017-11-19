---
title: "SCRIPTPROP_HOSTKEEPALIVE 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE 屬性
用來指定應該保存的指令碼引擎完整運作，如果有未處理的參考。  
  
 使用[IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md)將此屬性設定為`true`。 如果這個屬性設定為`true`，指令碼引擎會保留完整運作，只要至少一個未處理的參考至指令碼引擎本身或`IDispatch`指標所使用的指令碼建立的 JavaScript 物件引擎。 當這個屬性設定為`true`，您應該未明確關閉或重設的指令碼引擎使用[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)或[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)方法。 指令碼物件的最後一個參考版本關機指令碼引擎。  
  
## <a name="syntax"></a>語法  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>需求  
 這個屬性只會出現在 activscp.idl 一起安裝的版本[!INCLUDE[win8](../../javascript/includes/win8-md.md)]，與針對上的 Internet Explorer 8 KB 2707082 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或在 Internet Explorer 9 的 KB 2722913[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]或[!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]。