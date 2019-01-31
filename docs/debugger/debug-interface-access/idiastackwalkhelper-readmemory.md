---
title: IDiaStackWalkHelper::readMemory |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 229aace046dfebd75786dfa5c14998d9498b98b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967098"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
從記憶體中的可執行檔的映像中讀取資料的區塊。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 [in]值，以從[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)指定要讀取的記憶體類型的列舉類型。  
  
 va  
 [in]要從其中開始讀取的映像中的虛擬位址。  
  
 `cbData`  
 [in]以位元組為單位的資料緩衝區的大小。  
  
 `pcbData`  
 [out]傳回實際讀取的位元組數目。 如果`pbData`是`NULL`，則這是可用的資料的位元組總數。  
  
 `pbData`  
 [in、 out]讀取的記憶體會填入緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)