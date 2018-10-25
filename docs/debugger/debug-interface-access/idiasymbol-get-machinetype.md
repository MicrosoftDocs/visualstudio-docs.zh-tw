---
title: 'Idiasymbol:: Get_machinetype |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7969a82ac6103a81b7849bc9f983842c9ebd6e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876765"
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
擷取目標 CPU 的類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回值，以從[CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)指定的目標 CPU 類型的列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="see-also"></a>另請參閱  
 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)