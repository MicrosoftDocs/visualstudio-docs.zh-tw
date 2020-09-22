---
title: IDiaSymbol::get_age | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_age method
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82a15703fdb1738d92b6b7bbeda053625bb5fdda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838989"
---
# <a name="idiasymbolget_age"></a>IDiaSymbol::get_age
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

捕獲 .pdb 檔案的存留期值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 .pdb 檔案的存留期值。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 年齡不一定會對應到任何已知的時間值;它通常用來判斷 .pdb 檔案是否與對應的 .exe 檔案不同步。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
