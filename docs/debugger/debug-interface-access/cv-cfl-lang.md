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
ms.openlocfilehash: 34866bf7d43908d2fc7227f35f7df18f8942f981
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033173"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
指定程式碼的原始語言的應用程式或連結的模組。  
  
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
 CV_CFL_C  
 應用程式語言是 c。  
  
 CV_CFL_CXX  
 C + + 應用程式語言。  
  
 CV_CFL_FORTRAN  
 FORTRAN 應用程式語言。  
  
 CV_CFL_MASM  
 Microsoft Macro Assembler 應用程式語言。  
  
 CV_CFL_PASCAL  
 應用程式語言是依照 pascal 命名法。  
  
 CV_CFL_BASIC  
 應用程式語言為 BASIC。  
  
 CV_CFL_COBOL  
 COBOL 應用程式語言。  
  
 CV_CFL_LINK  
 應用程式是連結器產生的模組。  
  
 CV_CFL_CVTRES  
 應用程式是使用 CVTRES 工具轉換後的資源模組。  
  
 CV_CFL_CVTPGD  
 應用程式是以 CVTPGD 工具產生的 POGO 最佳化模組。  
  
 CV_CFL_CSHARP  
 應用程式語言是C#。  
  
 CV_CFL_VB  
 應用程式語言為 Visual Basic。  
  
 CV_CFL_ILASM  
 應用程式語言是中繼語言組件 （也就是 Common Language Runtime (CLR) 組件）。  
  
 CV_CFL_JAVA  
 Java 應用程式語言。  
  
 CV_CFL_JSCRIPT  
 應用程式語言為 Jscript。  
  
 CV_CFL_MSIL  
 應用程式語言是未知 Microsoft Intermediate Language (MSIL)，可能使用的結果[/LTCG （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)切換。  
  
 CV_CFL_HLSL  
 應用程式語言是高的層級著色器語言。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回呼叫[idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)