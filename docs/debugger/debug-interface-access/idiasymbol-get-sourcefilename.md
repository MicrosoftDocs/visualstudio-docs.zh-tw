---
title: IDiaSymbol::get_sourceFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sourceFileName method
ms.assetid: 0f5dce88-829e-4df3-8acd-8d71076ad167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f87d3bee740573d0d3597253ff4e0ce2049cbe4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461960"
---
# <a name="idiasymbolget_sourcefilename"></a>IDiaSymbol::get_sourceFileName
抓取編譯模組原始檔案的檔案名。

## <a name="syntax"></a>語法

```C++
HRESULT get_sourceFileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回編譯模組原始檔案的檔案名。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)