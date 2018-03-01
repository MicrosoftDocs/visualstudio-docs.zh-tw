---
title: "Idiaenumframedata:: Framebyva |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2dc2a371ac5ad322cde175c6da44d03c0235bd77
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
虛擬位址 (VA) 所傳回的框架。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>參數  
 virtualAddress  
 [in]VA 感興趣的畫面格。  
  
 框架  
 [out]傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，代表包含提供的地址的框架。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果沒有畫面格的資料符合指定的位址。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)