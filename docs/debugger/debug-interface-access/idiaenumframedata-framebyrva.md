---
title: 'Idiaenumframedata:: Framebyrva |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fba9982d26ebde88716e345cd449c488dc2bf8ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898675"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
傳回相對虛擬位址 (RVA) 在範圍內。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>參數  
 relativeVirtualAddress  
 [in]感興趣的畫面格的 RVA。  
  
 框架  
 [out]傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，表示框架，其中包含提供的地址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果沒有框架的資料符合指定的位址。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)