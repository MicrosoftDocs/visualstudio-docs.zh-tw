---
title: IActiveScriptSite::OnScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088409"
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