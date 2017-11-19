---
title: "Idiasymbol:: Get_virtualbasetabletype |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcbc4478830a730f684b008c88ff5c6490a1c596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
擷取虛擬基底資料表指標的類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`pRetVal`|[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，指定基底資料表的類型。|  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 虛擬基底資料表的指標 (`vbtptr`) 中的隱藏指標[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]vtable 處理從虛擬基底類別繼承。 A`vbtptr`可以具有不同大小根據繼承的類別。  
  
 這個方法會傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件可以用來判斷 vbtptr 的大小。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)