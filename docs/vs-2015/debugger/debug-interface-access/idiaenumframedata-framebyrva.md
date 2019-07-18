---
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 825f72eec5b56fef70019b64d6e599b7c4712ee2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146511"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

傳回相對虛擬位址 (RVA) 在範圍內。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果沒有框架的資料符合指定的位址。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
