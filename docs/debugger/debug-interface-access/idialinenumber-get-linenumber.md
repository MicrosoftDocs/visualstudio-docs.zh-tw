---
title: IDiaLineNumber::get_lineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumber method
ms.assetid: 2dff3fd9-097d-4645-bc1b-cb65ecbc42a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 60fcb463b4705a13cbdcf9802fb8fcf74df32246
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855729"
---
# <a name="idialinenumberget_linenumber"></a>IDiaLineNumber::get_lineNumber
捕獲原始程式檔中的行號。

## <a name="syntax"></a>語法

```C++
HRESULT get_lineNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回原始程式檔中的行號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="example"></a>範例

```C++
CComPtr< IDiaLineNumber> pLine;
DWORD linenum;
pLine->get_lineNumber( &linenum );
```

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)