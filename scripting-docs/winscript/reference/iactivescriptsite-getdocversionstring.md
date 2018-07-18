---
title: IActiveScriptSite::GetDocVersionString |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724538"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
擷取主應用程式定義的字串可唯一識別目前的文件版本。 如果相關文件已經變更 Windows 指令碼 （如同正在使用 「 記事本 」 編輯 HTML 網頁的情況下） 的範圍外，指令碼引擎可以儲存此以及其永續性狀態，強制重新編譯載入指令碼會在下一次。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrVersionString`  
 [out]主機定義文件的版本字串的位址。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_NOTIMPL`如果不支援這個方法。  
  
## <a name="remarks"></a>備註  
 如果`E_NOTIMPL`傳回，則指令碼引擎應該假設指令碼是與文件的同步處理。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)