---
title: SccRename 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e270d1be9cdf935dbffa7d094fddaecd4f73a02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433067"
---
# <a name="sccrename-function"></a>SccRename 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會將檔案重新命名原始檔控制系統中。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpFileName  
 [in]正在重新命名之檔案的完整的檔案名稱。  
  
 lpNewName  
 [in]完整的新名稱。 如果不同的目錄路徑，然後移動檔案從一個子目錄到另一個。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|重新命名作業已順利完成。|  
|SCC_E_PROJNOTOPEN|無法開啟原始檔控制下的專案。|  
|SCC_E_FILENOTCONTROLLED|檔案不是原始檔控制之下。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_NOTAUTHORIZED|使用者無權完成此作業。|  
|SCC_E_COULDNOTCREATEPROJECT|重新命名的程序的一部分，無法建立專案。|  
|SCC_E_OPNOTPERFORMED|未執行此作業。|  
|SCC_E_NONSPECIFICERROR|發生未指定或一般錯誤。|  
  
## <a name="remarks"></a>備註  
 此函式可用來重新命名檔案，或它從一個位置移到另一個原始檔控制系統中。 原始檔控制外掛程式不應嘗試存取磁碟上的檔案。 是 IDE 的責任，將本機檔案重新命名。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
