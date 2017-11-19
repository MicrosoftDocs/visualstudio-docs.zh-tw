---
title: "SccRename 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRename
helpviewer_keywords: SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2936c2ea4425ad6eaccc2d23853f4174e1c9c2a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccrename-function"></a>SccRename 函式
此函式會將檔案重新命名原始檔控制系統中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpFileName  
 [in]要重新命名檔案的完整的檔案名稱。  
  
 lpNewName  
 [in]完整的新名稱。 如果不同的目錄路徑，然後移動檔案從一個子目錄到另一個。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|重新命名作業順利完成。|  
|SCC_E_PROJNOTOPEN|無法在原始檔控制開啟專案。|  
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制中。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_NOTAUTHORIZED|使用者沒有完成這項作業。|  
|SCC_E_COULDNOTCREATEPROJECT|重新命名的程序的一部分，無法建立專案。|  
|SCC_E_OPNOTPERFORMED|未執行操作。|  
|SCC_E_NONSPECIFICERROR|發生未指定或一般錯誤。|  
  
## <a name="remarks"></a>備註  
 此函式可用來重新命名檔案，或將它從一個位置移到另一個原始檔控制系統中。 原始檔控制外掛程式不應嘗試存取磁碟上的檔案。 它負責 IDE 的重新命名本機檔案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)