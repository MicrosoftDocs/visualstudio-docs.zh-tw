---
title: IDiaStackWalkHelper::readMemory |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14a8e435dddaf0d6fb3908a1ccb6233f08ccd28b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468498"
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