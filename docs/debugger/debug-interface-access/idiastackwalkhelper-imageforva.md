---
title: IDiaStackWalkHelper：： imageForVA |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f28af62a4e5eaa89e92db533bf461dbecaf039d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464713"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
針對可執行檔的記憶體空間中某個位置的虛擬位址，傳回記憶體中可執行檔的映射開頭。

## <a name="syntax"></a>語法

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>參數
 `vaContext`

在位於可執行空間中某處的虛擬位址。

 `pvaImageStart`

脫銷傳回可執行檔影像的起始虛擬位址。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)