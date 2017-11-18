---
title: "IDiaStackWalkHelper::readMemory |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cccec7df8428db0a1e7c1fe2274475c2b723d760
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
讀取的可執行檔映像，在記憶體中的資料區塊。  
  
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
 [in]中的值[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)指定類型的記憶體讀取的列舉。  
  
 va  
 [in]從此處開始讀取映像中的虛擬位址。  
  
 `cbData`  
 [in]以位元組為單位的資料緩衝區的大小。  
  
 `pcbData`  
 [out]傳回實際讀取的位元組數目。 如果`pbData`是`NULL`，則這是可用的資料的位元組總數。  
  
 `pbData`  
 [in、 out]讀取的記憶體填入緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)