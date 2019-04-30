---
title: IActiveScriptSite::OnScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992599"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
通知主機引擎正在執行指令碼時發生執行錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pase`  
 [in]錯誤物件的位址[IActiveScriptError](../../winscript/reference/iactivescripterror.md)介面。 主機可以使用此介面，來取得執行錯誤的相關資訊。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`正確處理此錯誤，則否則 OLE 定義的錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)