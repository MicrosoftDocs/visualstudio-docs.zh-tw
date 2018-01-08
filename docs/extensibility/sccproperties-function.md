---
title: "SccProperties 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccProperties
helpviewer_keywords: SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efaa2877743fcf69a61a79633108d203442489e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccproperties-function"></a>SccProperties 函式
此函式會顯示檔案或專案的原始檔控制屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpFileName  
 [in]檔案或專案的完整的路徑名稱。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功顯示內容。|  
|SCC_I_RELOADFILE|在版本控制系統已修改檔案內容中，因此 IDE 應重新載入此檔案。|  
|SCC_E_PROJNOTOPEN|指定的專案尚未開啟原始檔控制中。|  
|SCC_E_NOTAUTHORIZED|使用者沒有檢視此檔案或專案的屬性。|  
|SCC_E_FILENOTCONTROLLED|指定的檔案或專案不是原始檔控制之下。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|發生未知或一般錯誤。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式在它自己的對話方塊中顯示的屬性。  
  
 屬性由原始檔控制外掛程式所定義，而且可能會有所不同外掛程式外掛程式。 如果外掛程式可讓使用者變更原始檔控制的內容檔案，它應該傳回`SCC_I_RELOAD`來表示此檔案或專案需要重新載入在 IDE。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)