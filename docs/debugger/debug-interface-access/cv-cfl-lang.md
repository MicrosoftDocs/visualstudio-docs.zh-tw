---
title: CV_CFL_LANG |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ba4637baf2fa7aec7688648096cd34341442d05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="cvcfllang"></a>CV_CFL_LANG
指定原始程式碼語言的應用程式或連結的模組。  
  
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
 應用程式語言為 c。  
  
 CV_CFL_CXX  
 應用程式語言為 c + +。  
  
 CV_CFL_FORTRAN  
 應用程式語言為 FORTRAN。  
  
 CV_CFL_MASM  
 應用程式語言為 Microsoft Macro 組件。  
  
 CV_CFL_PASCAL  
 應用程式的語言是依照 pascal 命名法。  
  
 CV_CFL_BASIC  
 應用程式語言為 BASIC。  
  
 CV_CFL_COBOL  
 應用程式語言為 COBOL。  
  
 CV_CFL_LINK  
 應用程式是連結器產生的模組。  
  
 CV_CFL_CVTRES  
 應用程式是使用 CVTRES 工具轉換資源模組。  
  
 CV_CFL_CVTPGD  
 應用程式是以 CVTPGD 工具產生的最佳化 POGO 模組。  
  
 CV_CFL_CSHARP  
 應用程式語言為 C#。  
  
 CV_CFL_VB  
 應用程式語言為 Visual Basic。  
  
 CV_CFL_ILASM  
 應用程式語言是中繼語言組件 （也就是 Common Language Runtime (CLR) 組件）。  
  
 CV_CFL_JAVA  
 應用程式的語言是 Java。  
  
 CV_CFL_JSCRIPT  
 應用程式語言為 Jscript。  
  
 CV_CFL_MSIL  
 應用程式的語言是未知 Microsoft Intermediate Language (MSIL)，可能是使用所造成的[/LTCG （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)切換。  
  
 CV_CFL_HLSL  
 應用程式語言為高的層級著色器語言。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳回透過呼叫[idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)