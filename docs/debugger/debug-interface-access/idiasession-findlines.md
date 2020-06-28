---
title: IDiaSession：： findLines |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a9867c3997a73f349ba7a9989cb8450f9bd2d3c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465675"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
抓取指定編譯模組和原始程式檔識別碼內的行號。

## <a name="syntax"></a>語法

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `compiland`

在代表編譯模組的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 使用此介面做為用來搜尋行號的內容。

 `file`

在[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表要在其中搜尋行號的來源檔案。

 `ppResult`

脫銷傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含所抓取的行號清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)