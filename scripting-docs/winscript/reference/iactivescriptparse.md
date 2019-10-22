---
title: IActiveScriptParse |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561647"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
如果 Windows 腳本引擎允許將原始文字程式碼程式碼片段加入至腳本，或允許在執行時間評估運算式文字，則會執行 `IActiveScriptParse` 介面。 對於沒有獨立撰寫環境的解讀式指令碼語言（例如 VBScript），這會提供替代機制（而不是 `IPersist*`），以將腳本程式碼放入腳本引擎中，並將腳本片段附加至各種物件事件.  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|初始化腳本引擎。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|將程式碼程式碼片段加入至腳本。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|剖析指定的程式碼程式碼片段、將宣告新增至命名空間，並適當地評估程式碼。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)