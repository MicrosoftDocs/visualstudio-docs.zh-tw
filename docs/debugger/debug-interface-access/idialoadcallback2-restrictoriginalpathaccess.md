---
title: "Idialoadcallback2:: Restrictoriginalpathaccess |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 826cebba9d4eaf8e2bcf6d055a2ce524e1cf17d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
決定是否可以尋找.pdb 檔案中原始的偵錯目錄。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 任何傳回碼以外`S_OK`防止搜尋原始的偵錯目錄中的.pdb 檔案。 原始的偵錯目錄是編譯成可執行檔時開啟偵錯符號檔的路徑。 此路徑不一定可執行檔所在的路徑相同。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)