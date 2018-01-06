---
title: "CRT 偵錯程式庫使用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 420dcc98aad4f4ca2ad76d16b7f4c6c7c51d2beb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="crt-debug-library-use"></a>CRT 偵錯程式庫操作
C 執行階段程式庫提供更多的偵錯支援。 若要使用其中一種 CRT 偵錯程式庫，您必須連結[偵錯](/cpp/build/reference/debug-generate-debug-info)然後使用編譯**/MDd**， **/MTd**，或**/LDd**。  
  
## <a name="remarks"></a>備註  
 可以在 CRTDBG.h 標頭檔裡找到 CRT 偵錯的主要定義和巨集。  
  
 CRT 偵錯程式庫中的函式會編譯偵錯資訊 ([/Z7、 /Zd、 /Zi、 /ZI （偵錯資訊格式）](/cpp/build/reference/z7-zi-zi-debug-information-format)) 並不需要最佳化。 有些函式包含可驗證傳入它們的參數之判斷提示，而且提供原始程式碼。 有了這個原始程式碼，您可以逐步執行 CRT 函式來確認函式是否如您希望的方式來執行，並檢查錯誤參數或記憶體狀態 (有些 CRT 技術是專屬的，且沒有提供例外狀況處理、浮點和其他一些常式的原始程式碼)。  
  
 安裝 Visual C++ 時，您可以選擇在硬碟安裝 C 執行階段程式庫原始程式碼的選項。 如果您沒有安裝原始程式碼，您會需要 CD-ROM 來逐步執行 CRT 函式。  
  
 如需有關您可以使用的各種執行階段程式庫的詳細資訊，請參閱[C 執行階段程式庫](/cpp/c-runtime-library/crt-library-features)。  
  
## <a name="see-also"></a>請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)   
 [/MD、 /MT、 /LD （使用執行階段程式庫）](/cpp/build/reference/md-mt-ld-use-run-time-library)