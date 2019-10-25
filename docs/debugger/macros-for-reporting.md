---
title: 報告的宏 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731394"
---
# <a name="macros-for-reporting"></a>報告巨集
若要進行偵錯工具，您可以使用 **_RPTn**和 **_RPTFn**宏（定義于 crtdbg.h 裡中）。H：取代 `printf` 語句的用法。 您不需要在 **#ifdef**s 中 inclose 它們，因為當 **_debug**未定義時，它們會自動在您的發行組建中消失。

|巨集|描述|
|-----------|-----------------|
|**_RPT0**、 **_RPT1**、 **_RPT2**、 **_RPT3**、 **_RPT4**|輸出訊息字串和零至四個引數。 從 _RPT1 到 **_RPT4**，訊息字串作為引數的 printf 樣式格式字串。|
|**_RPTF0**、 **_RPTF1**、 **_RPTF2**、 **_RPTF4**|與 **_RPTn** 相同，但是這些巨集也會輸出巨集所在位置的檔案名稱和行號。|

 參考下列範例：

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 這段程式碼會將 `someVar` 和 `otherVar` 的值輸出至 **stdout**。 您可以使用下列的 `_RPTF2` 呼叫來報告這些相同的值，此外，還有檔名和行號：

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

您可能會發現特定的應用程式需要 debug 報告，而 C 執行時間程式庫所提供的宏並未提供。 在這些情況下，您可以撰寫專為符合您自己的需求而設計的宏。 例如，您可以在其中一個標頭檔案中，包含如下的程式碼，來定義名為 **ALERT_IF2** 的巨集：

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 **ALERT_IF2**的一次呼叫可以執行**printf**程式碼的所有功能：

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 您可以輕鬆地變更自訂宏，將更多或更少的資訊報告至不同的目的地。 當您的偵錯工具需求演進時，這個方法特別有用。

## <a name="see-also"></a>請參閱
- [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
