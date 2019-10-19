---
title: IActiveScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576906"
---
# <a name="iactivescripterror"></a>IActiveScriptError
每當腳本引擎遇到未處理的錯誤時，就會將執行此介面的物件傳遞至[IActiveScriptSite：： OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)方法。 然後，主機會在此物件上呼叫方法，以取得所發生錯誤的相關資訊。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|抓取有關錯誤的資訊。|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|在原始程式碼中捕獲發生錯誤的位置。|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|在原始程式檔中，捕獲發生錯誤的行。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)