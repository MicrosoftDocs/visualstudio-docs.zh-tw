---
title: CRT Debug 程式庫使用 |Microsoft Docs
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7e58f65f174c549f6992e9218d7ad692634e20d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435879"
---
# <a name="crt-debug-library-use"></a>CRT 偵錯程式庫操作
C 執行階段程式庫提供更多的偵錯支援。 若要使用其中一個 CRT debug 程式庫，您必須使用[/debug](/cpp/build/reference/debug-generate-debug-info)連結，並使用 **/MDd**、 **/MTd**或 **/LDd**進行編譯。

## <a name="remarks"></a>備註
 可以在 CRTDBG.h 標頭檔裡找到 CRT 偵錯的主要定義和巨集。

 CRT 偵錯程式庫裡的函式會在沒有最佳化情況下以偵錯資訊 ([/Z7、/Zd、/Zi、/ZI (偵錯資訊格式)](/cpp/build/reference/z7-zi-zi-debug-information-format)) 進行編譯。 有些函式包含可驗證傳入它們的參數之判斷提示，而且提供原始程式碼。 有了這個原始程式碼，您可以逐步執行 CRT 函式來確認函式是否如您希望的方式來執行，並檢查錯誤參數或記憶體狀態 (有些 CRT 技術是專屬的，且沒有提供例外狀況處理、浮點和其他一些常式的原始程式碼)。

 如需各種可以使用的執行階段程式庫之詳細資訊，請參閱 [C Run-Time Libraries](/cpp/c-runtime-library/crt-library-features) (C 執行階段程式庫)。

## <a name="see-also"></a>請參閱

- [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
- [/MD、/MT、/LD (使用執行階段程式庫)](/cpp/build/reference/md-mt-ld-use-run-time-library)