---
title: 'Idiasectioncontrib:: Get_informational |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcadd756ab9bea1d02dddb79728dcc68be8220b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788442"
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取旗標，指出區段是否包含註解或類似的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`如果區段包含註解或其他資訊中; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常.directive 區段包含的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



