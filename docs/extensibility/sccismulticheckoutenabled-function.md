---
title: "SccIsMultiCheckoutEnabled 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b04cd593bd631ba92545901ff289a9f8ed4f1822
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
此函式會檢查原始檔控制外掛程式是否允許多重簽出檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 pbMultiCheckout  
 [out]指定是否啟用多重簽出這個專案 （為非零，表示支援的多重簽出）。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|檢查成功。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 IDE，可讓兩個檢查並判斷是否檔案可以簽出同時由多個使用者。 首先，原始檔控制系統必須支援多重簽出。 原始檔控制外掛程式可以藉由指定初始化過程中指定這項功能`SCC_CAP_MULTICHECKOUT`。 之後，第二個檢查時，IDE 會呼叫此函式可判斷目前的專案支援多重簽出。 如果支援多重簽出，則選取專案，則外掛程式會傳回成功一個程式碼，並設定`pbMultiCheckout`為非零 (`TRUE`) 或`FALSE`。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)