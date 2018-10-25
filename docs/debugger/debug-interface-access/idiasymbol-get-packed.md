---
title: 'Idiasymbol:: Get_packed |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c17d60509345e1a51df615c0d2aca90e32d055f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835848"
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
擷取旗標，指定是否要封裝的使用者定義資料類型 (UDT)。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`UDT 已壓縮; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="remarks"></a>備註  
 封裝的表示 UDT 的所有成員都位於關閉共同盡可能的情況下，要對齊記憶體界限沒有中介填補。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)