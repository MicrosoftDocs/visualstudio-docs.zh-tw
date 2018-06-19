---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f5e6ceefbff4702d509c18b4a555287a1e9f42
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466639"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
虛設常式函式 c + + AMP 中傳回 accelerator 指標標記數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>參數  
 `count`  
 [out]指標`DWORD`的虛設常式函式 c + + AMP 中保存的加速器數目指標標記。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會在呼叫`IDiaSymbol`對應至 c + + AMP 加速器虛設常式函式的介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)