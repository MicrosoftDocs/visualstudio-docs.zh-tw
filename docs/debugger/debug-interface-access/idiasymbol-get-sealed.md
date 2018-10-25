---
title: 'Idiasymbol:: Get_sealed |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e77e379d3f3635cf6976765450ba32ea6de81ef2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841802"
---
# <a name="idiasymbolgetsealed"></a>IDiaSymbol::get_sealed
擷取指定是否已密封類別或方法的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sealed(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`已密封類別或方法; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 密封類別不能當做基底類別使用。 密封的方法不能覆寫此屬性。  
  
## <a name="requirements"></a>需求  
 標頭： Dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)