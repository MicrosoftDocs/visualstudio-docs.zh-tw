---
title: IActiveScriptSite::GetDocVersionString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7327b71329c1f476eab9c27d5e0d5a047664abfa
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147952"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
擷取主應用程式定義的字串可唯一識別目前的文件版本。 如果相關的文件已變更的 Windows 指令碼 （如同使用 「 記事本 」 編輯 HTML 網頁的大小寫） 範圍外，指令碼引擎可以儲存此以及其保存的狀態，強制重新編譯指令碼會載入在下一次。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrVersionString`  
 [out]主應用程式定義的文件的版本字串的位址。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_NOTIMPL`不支援此方法。  
  
## <a name="remarks"></a>備註  
 如果`E_NOTIMPL`傳回時，指令碼引擎應該假設指令碼與文件的同步處理。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)