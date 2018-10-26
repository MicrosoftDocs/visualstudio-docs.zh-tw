---
title: SccIsMultiCheckoutEnabled 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 642f42de508702bfd1dd344b489ec875de9deedc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845767"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會檢查原始檔控制外掛程式是否允許多重簽出檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 pbMultiCheckout  
 [out]指定是否啟用多重簽出，以供這個專案 （非零值表示，支援多重簽出）。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|檢查成功。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 IDE 會判斷如果檔案可以簽出同時由多個使用者的兩個檢查。 首先，原始檔控制系統必須支援多重簽出。 原始檔控制外掛程式可以藉由指定初始化過程中指定這項功能`SCC_CAP_MULTICHECKOUT`。 此後，做為第二個檢查，IDE 會呼叫此函式可判斷目前的專案支援多重簽出。 如果選取的專案支援多重簽出，外掛程式會傳回成功的程式碼，並設定`pbMultiCheckout`為非零 (`TRUE`) 或`FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)

