---
title: "IActiveScriptSite::OnScriptError |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
通知主機在引擎執行指令碼時發生執行錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pase`  
 [in]錯誤物件的位址[IActiveScriptError](../../winscript/reference/iactivescripterror.md)介面。 主機可以使用此介面來取得有關執行錯誤。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果正確處理此錯誤，否則 OLE 定義的錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)