---
title: IDiaSymbol：： get_textureSlot |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 050e2b4db8a29ab0b80774f4e135624109729405
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461813"
---
# <a name="idiasymbolget_textureslot"></a>IDiaSymbol::get_textureSlot
抓取材質位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_textureSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷包含材質位置之的指標 `DWORD` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)