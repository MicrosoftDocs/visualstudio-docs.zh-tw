---
title: IDiaLoadCallback2::RestrictOriginalPathAccess |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb703ea0ffdab842e735a896c26066173943205e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489065"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaLoadCallback2::RestrictOriginalPathAccess](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess)。  
  
判斷是否可以尋找在原始的偵錯目錄中的.pdb 檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 任何傳回碼以外`S_OK`防止尋找原始的偵錯目錄中的.pdb 檔案。 原始的偵錯目錄是編譯成可執行檔，當開啟偵錯符號檔的路徑。 此路徑不一定可執行檔所在的路徑相同。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



