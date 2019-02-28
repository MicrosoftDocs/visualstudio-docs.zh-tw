---
title: 'Idiastackwalkframe:: Readmemory |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82ef0d25e796f9e04ecdcfd0c54a7312b9c9edad
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628594"
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

## <a name="see-also"></a>請參閱
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)