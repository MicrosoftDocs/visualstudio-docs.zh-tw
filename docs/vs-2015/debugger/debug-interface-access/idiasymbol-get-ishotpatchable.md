---
title: 'Idiasymbol:: Get_ishotpatchable |Microsoft Docs'
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
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c33c26ba9c46d5ae4183cec60a01052af50f30b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915902"
---
# <a name="idiasymbolgetishotpatchable"></a>IDiaSymbol::get_isHotpatchable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

旗標，指出是否已編譯的模組會擷取[/hotpatch （建立可線上修補的影像）](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798)編譯器參數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`如果模組是經常性存取-可修補; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 這個屬性會使用來自`SymTagCompilandDetails`符號類型 (請參閱 < [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md))。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)



