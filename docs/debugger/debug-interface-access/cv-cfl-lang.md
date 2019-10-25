---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745340"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
指定應用程式或連結模組的原始程式碼語言。

## <a name="syntax"></a>語法

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>項目
CV_CFL_C 應用程式語言為 C。

CV_CFL_CXX 應用程式語言C++是。

CV_CFL_FORTRAN 應用程式語言是 FORTRAN。

CV_CFL_MASM 應用程式語言是 Microsoft 巨集群組合器。

CV_CFL_PASCAL 應用程式語言是 Pascal。

CV_CFL_BASIC 應用程式語言是基本的。

CV_CFL_COBOL 應用程式語言是 COBOL。

CV_CFL_LINK 應用程式是連結器產生的模組。

CV_CFL_CVTRES 應用程式是以 CVTRES 工具轉換的資源模組。

CV_CFL_CVTPGD 應用程式是使用 CVTPGD 工具所產生的 POGO 優化模組。

CV_CFL_CSHARP 應用程式語言C#是。

CV_CFL_VB 應用程式語言 Visual Basic。

CV_CFL_ILASM 應用程式語言是中繼語言元件（也就是 Common Language Runtime （CLR）元件）。

CV_CFL_JAVA 應用程式語言為 JAVA。

CV_CFL_JSCRIPT 應用程式語言為 Jscript。

CV_CFL_MSIL 應用程式語言是未知的 Microsoft 中繼語言（MSIL），可能是使用[/ltcg （連結時產生程式碼）](/cpp/build/reference/ltcg-link-time-code-generation)參數的結果。

CV_CFL_HLSL 應用程式語言是高層級的著色器語言。

## <a name="remarks"></a>備註
這個列舉中的值是由呼叫[IDiaSymbol：： get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
