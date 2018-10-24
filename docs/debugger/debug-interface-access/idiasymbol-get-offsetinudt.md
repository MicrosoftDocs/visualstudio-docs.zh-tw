---
title: 'Idiasymbol:: Get_offsetinudt |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offsetInUdt method
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48b13de8a9d1680ae4e2a6a94a4fda120a74a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911417"
---
# <a name="idiasymbolgetoffsetinudt"></a>IDiaSymbol::get_offsetInUdt
擷取至使用者定義型別 (UDT) 中的 UDT 的成員開頭的位移。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_offsetInUdt(   
   DWORD* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回以位元組為單位的符號位置的位移。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 此函式只能用於最佳化組建中的本機記錄。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)