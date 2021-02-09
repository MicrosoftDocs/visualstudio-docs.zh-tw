---
title: CV_CFL_LANG | Microsoft Docs
description: 取得 CV_CFL_LANG 列舉型別的相關資訊，這個型別會在 debug interface access SDK 中指定應用程式或連結模組的程式碼語言。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46c20fbe0c46a6c964a05b92ccd3a8bcf73cd1f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857367"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
指定應用程式或連結模組的原始程式碼語言。

## <a name="syntax"></a>Syntax

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

## <a name="elements"></a>元素
CV_CFL_C 的應用程式語言是 C。

CV_CFL_CXX 的應用程式語言是 c + +。

CV_CFL_FORTRAN 的應用程式語言是 FORTRAN。

CV_CFL_MASM 的應用程式語言是 Microsoft 巨集群組合器。

CV_CFL_PASCAL 的應用程式語言為 Pascal。

CV_CFL_BASIC 的應用程式語言是基本的。

CV_CFL_COBOL 的應用程式語言是 COBOL。

CV_CFL_LINK 應用程式是連結器產生的模組。

CV_CFL_CVTRES 應用程式是以 CVTRES 工具轉換的資源模組。

CV_CFL_CVTPGD 應用程式是使用 CVTPGD 工具產生的 POGO 優化模組。

CV_CFL_CSHARP 的應用程式語言是 c #。

Visual Basic CV_CFL_VB 應用程式語言。

CV_CFL_ILASM 應用程式語言是中繼語言元件 (也就是 Common Language Runtime (CLR) 元件) 。

CV_CFL_JAVA 的應用程式語言是 JAVA。

CV_CFL_JSCRIPT 的應用程式語言為 Jscript。

CV_CFL_MSIL 應用程式語言是未知的 Microsoft 中繼語言 (MSIL) ，可能是因為使用 [/ltcg (連結時產生程式碼) ](/cpp/build/reference/ltcg-link-time-code-generation) 切換。

CV_CFL_HLSL 應用程式語言為高階著色器語言。

## <a name="remarks"></a>備註
呼叫 [IDiaSymbol：： get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) 方法時，會傳回此列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
