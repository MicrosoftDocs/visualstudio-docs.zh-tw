---
title: SccProperties 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb8fd8172468dc1fc4d60d0f5e36ee7b4f9a588
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486790"
---
# <a name="sccproperties-function"></a>SccProperties 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccProperties 函式](https://docs.microsoft.com/visualstudio/extensibility/sccproperties-function)。  
  
此函式會顯示檔案或專案的原始檔控制屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpFileName  
 [in]檔案或專案的完整的路徑名稱。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功透過顯示屬性。|  
|SCC_I_RELOADFILE|版本控制系統已修改檔案內容，讓 IDE 應重新載入這個檔案。|  
|SCC_E_PROJNOTOPEN|指定的專案尚未開啟原始檔控制中。|  
|SCC_E_NOTAUTHORIZED|使用者未獲授權檢視此檔案或專案的屬性。|  
|SCC_E_FILENOTCONTROLLED|指定的檔案或專案不是原始檔控制之下。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|發生未知或一般錯誤。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式在它自己的對話方塊中顯示的屬性。  
  
 屬性由原始檔控制外掛程式所定義，並可能不同於外掛程式，外掛程式。 如果外掛程式可讓使用者變更檔案的原始檔控制屬性，它應該傳回`SCC_I_RELOAD`發出信號的 IDE，此檔案或專案需要重新載入。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)

