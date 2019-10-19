---
title: IActiveScript：： SetScriptSite |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575323"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
通知主機所提供之[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面網站的腳本引擎。 在使用任何其他[IActiveScript](../../winscript/reference/iactivescript.md)介面方法之前，請先呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pScriptSite`  
 在與這個腳本引擎實例相關聯的主機提供的腳本網站位址。 網站必須是唯一指派給這個腳本引擎實例;它無法與其他腳本引擎共用。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|發生未指定的錯誤;腳本引擎無法完成網站的初始化。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，已設定網站）。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)