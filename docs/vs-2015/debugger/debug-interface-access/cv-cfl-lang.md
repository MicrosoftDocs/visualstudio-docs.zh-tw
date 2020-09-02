---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699352"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定應用程式或連結模組的原始程式碼語言。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 CV_CFL_C  
 應用程式語言是 C。  
  
 CV_CFL_CXX  
 應用程式語言是 c + +。  
  
 CV_CFL_FORTRAN  
 應用程式語言是 FORTRAN。  
  
 CV_CFL_MASM  
 應用程式語言是 Microsoft 巨集群組合器。  
  
 CV_CFL_PASCAL  
 應用程式語言為 Pascal。  
  
 CV_CFL_BASIC  
 應用程式語言是基本的。  
  
 CV_CFL_COBOL  
 應用程式語言是 COBOL。  
  
 CV_CFL_LINK  
 應用程式是連結器產生的模組。  
  
 CV_CFL_CVTRES  
 應用程式是以 CVTRES 工具轉換的資源模組。  
  
 CV_CFL_CVTPGD  
 應用程式是使用 CVTPGD 工具產生的 POGO 優化模組。  
  
 CV_CFL_CSHARP  
 應用程式語言是 c #。  
  
 CV_CFL_VB  
 Visual Basic 的應用程式語言。  
  
 CV_CFL_ILASM  
 應用程式語言是中繼語言元件 (也就是 (CLR) 元件) 的 Common Language Runtime。  
  
 CV_CFL_JAVA  
 應用程式語言是 JAVA。  
  
 CV_CFL_JSCRIPT  
 應用程式語言為 Jscript。  
  
 CV_CFL_MSIL  
 應用程式語言是未知的 Microsoft 中繼語言 (MSIL) ，可能是使用 [/ltcg (連結時產生程式碼) ](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) 參數的結果。  
  
 CV_CFL_HLSL  
 應用程式語言為高階著色器語言。  
  
## <a name="remarks"></a>備註  
 呼叫 [IDiaSymbol：： get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) 方法時，會傳回此列舉中的值。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst。h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
