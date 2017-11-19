---
title: "IActiveScriptParse32 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
如果 Windows 指令碼引擎可讓未經處理的文字加入指令碼的程式碼程式碼片段，或允許在執行階段評估的運算式文字，它會實作`IActiveScriptParse32`介面。 這在具有任何獨立的撰寫環境，例如，VBScript、 解譯指令碼語言提供替代機制 (以外`IPersist*`) 到指令碼引擎中，取得指令碼，並將附加到不同的物件的指令碼片段事件。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|將程式碼的程式碼片段加入至指令碼。|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|初始化指令碼引擎。|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|剖析指定的程式碼程式碼片段，加入到此命名空間宣告，並評估為適當的程式碼。|