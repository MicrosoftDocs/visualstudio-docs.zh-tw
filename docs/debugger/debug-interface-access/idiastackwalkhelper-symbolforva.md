---
title: IDiaStackWalkHelper::symbolForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90b157b0f5b09353ede1af1d344f1f9adf68debd
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464629"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
抓取包含指定之虛擬位址的符號。

## <a name="syntax"></a>語法

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>參數
 `va`

在要求的符號中包含的虛擬位址。 符號必須是 `SymTagFunctionType` （來自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉的值）。

 `ppSymbol`

脫銷[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示位於指定位址的符號。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)