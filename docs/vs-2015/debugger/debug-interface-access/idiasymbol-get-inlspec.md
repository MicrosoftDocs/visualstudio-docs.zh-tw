---
title: IDiaSymbol：： get_InlSpec |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 99a92f134390e5d3215b1609234e643b71d93d3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838875"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此函式會抓取旗標，指出是否已使用其中一個 [內嵌、__inline \_ _forceinline](../../misc/inline-inline-forceinline.md) 屬性) ，將函數標記為內嵌 (。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_inlSpec(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展如果函式 `TRUE` 標記為內嵌，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [內嵌、__inline、 \_ _forceinline](../../misc/inline-inline-forceinline.md)
