---
title: IDiaLineNumber::get_sourceFileId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a0151a8cd5bcc10fb306b34762ad5d1bb698f4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466851"
---
# <a name="idialinenumberget_sourcefileid"></a>IDiaLineNumber::get_sourceFileId
針對產生這一行的原始程式檔，抓取唯一的原始程式檔識別碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_sourceFileId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回產生這一行之原始程式檔的唯一原始程式檔識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)