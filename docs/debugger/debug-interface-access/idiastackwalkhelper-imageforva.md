---
description: 針對可執行檔記憶體空間中某處的虛擬位址，傳回記憶體中的可執行檔映射的起始位置。
title: IDiaStackWalkHelper：： imageForVA |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2459ed59f4b34befd893d25848de9482b39f9d70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156843"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
針對可執行檔記憶體空間中某處的虛擬位址，傳回記憶體中的可執行檔映射的起始位置。

## <a name="syntax"></a>語法

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>參數
 `vaContext`

在位於可執行檔空間中某處的虛擬位址。

 `pvaImageStart`

擴展傳回可執行檔映射的起始虛擬位址。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
