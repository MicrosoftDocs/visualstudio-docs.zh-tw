---
title: SCRIPTPROP_HOSTKEEPALIVE 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c8918e277fa9c7183e6d46a4853824a74fa4548
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087369"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE 屬性
用來指定應該保留指令碼引擎有未完成的參考的完整功能。  
  
 使用[IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md)若要將此屬性設定為`true`。 如果這個屬性設定為`true`，指令碼引擎處於完全正常運作，只要至少一個未完成的參考至指令碼引擎本身或`IDispatch`指標所使用的指令碼建立的 JavaScript 物件引擎。 當這個屬性設定為`true`，您應該不明確關閉，或使用重設指令碼引擎[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)或是[iactivescript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md)方法。 發行的指令碼物件的最後一個參考關機指令碼引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>需求  
 這個屬性只會出現在 activscp.idl 一起安裝的版本[!INCLUDE[win8](../../javascript/includes/win8-md.md)]，使用 Internet Explorer 8 的 KB 2707082 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或使用上的 Internet Explorer 9 的 KB 2722913[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]或[!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]。