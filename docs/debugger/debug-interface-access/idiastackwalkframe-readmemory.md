---
title: 'Idiastackwalkframe:: Readmemory |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 163895ecf16849e122c5ede042b1bc4842c2a5e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818311"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
讀取影像中的記憶體。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 [in]其中一個[MemoryTypeEnum 列舉](../../debugger/debug-interface-access/memorytypeenum.md)列舉值，指定一種記憶體存取。  
  
 `va`  
 [in]若要開始讀取的映像中的虛擬位址位置。  
  
 `cbData`  
 [in]資料緩衝區，以位元組為單位的大小。  
  
 `pcbData`  
 [out]傳回動作傳回的位元組的數目。 如果`data`已`NULL`，然後`pcbData`包含可用資料的位元組總數。  
  
 `data`  
 [out]要從指定位置的資料填入的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)