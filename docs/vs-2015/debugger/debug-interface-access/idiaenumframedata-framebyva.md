---
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0560965858bd6d9ee823a6056332bdd9a7b654a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146496"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

依虛擬位址 (VA) 傳回框架。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>參數  
 virtualAddress  
 在感興趣的框架 VA。  
  
 框架  
 擴展傳回 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件，這個物件表示包含所提供位址的框架。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有框架資料符合指定的位址則傳回。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
