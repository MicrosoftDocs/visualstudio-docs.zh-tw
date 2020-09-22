---
title: IDiaSymbol::get_hasDebugInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasDebugInfo method
ms.assetid: 84cd2b67-0d83-4589-9ecb-a4bcbeed55f5
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06cbf9fd26e675168975aa2c4a8c30033bbefe3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838970"
---
# <a name="idiasymbolget_hasdebuginfo"></a>IDiaSymbol::get_hasDebugInfo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取旗標，這個旗標會指定 [編譯單位](../../debugger/debug-interface-access/compiland.md) 是否包含偵錯工具資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT get_hasDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 擴展 `TRUE` 如果編譯單位包含調試資訊，則傳回，否則傳回 `FALSE` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
