---
title: CRT Debug 程式庫使用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697850"
---
# <a name="crt-debug-library-use"></a>CRT 偵錯程式庫操作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C 執行階段程式庫提供更多的偵錯支援。 若要使用其中一個 CRT debug 程式庫，您必須與 [/debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) 連結，並使用 **/MDd**、 **/MTd**或 **/LDd**進行編譯。  
  
## <a name="remarks"></a>備註  
 可以在 CRTDBG.h 標頭檔裡找到 CRT 偵錯的主要定義和巨集。  
  
 CRT 偵錯程式庫裡的函式會在沒有最佳化情況下以偵錯資訊 ([/Z7、/Zd、/Zi、/ZI (偵錯資訊格式)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) 進行編譯。 有些函式包含可驗證傳入它們的參數之判斷提示，而且提供原始程式碼。 有了這個原始程式碼，您可以逐步執行 CRT 函式來確認函式是否如您希望的方式來執行，並檢查錯誤參數或記憶體狀態 (有些 CRT 技術是專屬的，且沒有提供例外狀況處理、浮點和其他一些常式的原始程式碼)。  
  
 安裝 Visual C++ 時，您可以選擇在硬碟安裝 C 執行階段程式庫原始程式碼的選項。 如果您沒有安裝原始程式碼，您會需要 CD-ROM 來逐步執行 CRT 函式。  
  
 如需各種可以使用的執行階段程式庫之詳細資訊，請參閱 [C Run-Time Libraries](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f) (C 執行階段程式庫)。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 調試技術](../debugger/crt-debugging-techniques.md)   
 [/MD、/MT、/LD (使用執行時間程式庫) ](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
