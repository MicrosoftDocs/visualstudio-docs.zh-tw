---
title: 'Iactivescript:: Setscriptsite |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b2a96732e904c7249dc5228ef414c3315012ec56
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097431"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
通知的指令碼引擎[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)主應用程式所提供的介面站台。 呼叫這個方法在任何其他[IActiveScript](../../winscript/reference/iactivescript.md)介面方法使用。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pScriptSite`  
 [in]要與這個指令碼引擎的執行個體相關聯的主機提供的指令碼網站位址。 站台必須唯一地指派給此指令碼引擎執行個體;它不能與其他指令碼引擎共用。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|發生意外的錯誤;指令碼引擎無法完成初始化站台。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，已經設定站台）。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)