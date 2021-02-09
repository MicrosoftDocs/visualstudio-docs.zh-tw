---
title: 適用于報表的宏 |Microsoft Docs
description: 瞭解 CRTDBG.H 裡中所提供的調試宏 _RPTn 和 _RPTFn。H，以及建立您自己的偵錯工具宏。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0356f05c3f0dac636813d1632f628dd02dd28923
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893122"
---
# <a name="macros-for-reporting"></a>報告巨集
若要進行偵錯工具，您可以使用 CRTDBG.H 裡中定義的 **_RPTn** 和 **_RPTFn** 宏。H，取代語句的使用 `printf` 。 您不需要在 **#ifdef** 中 inclose 它們，因為 **_DEBUG** 未定義時，它們會自動在您的發行組建中消失。

|巨集|Description|
|-----------|-----------------|
|**_RPT0**、**_RPT1**、**_RPT2**、**_RPT3**、**_RPT4**|輸出訊息字串和零至四個引數。 針對 **_RPT1** 至 **_RPT4**，訊息字串可作為引數的 printf 樣式格式字串。|
|**_RPTF0**、 **_RPTF1**、 **_RPTF2**、 **_RPTF3**、 **_RPTF4**|與 **_RPTn** 相同，但是這些巨集也會輸出巨集所在位置的檔案名稱和行號。|

 請考慮下列範例：

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

您可能會發現特定應用程式需要 debug 報告，但 C 執行時間程式庫所提供的宏未提供。 在這些情況下，您可以撰寫專為符合您自己的需求而設計的宏。 例如，您可以在其中一個標頭檔案中，包含如下的程式碼，來定義名為 **ALERT_IF2** 的巨集：

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

 **ALERT_IF2** 的一個呼叫可以執行 **printf** 程式碼的所有功能：

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 您可以輕鬆地變更自訂宏，將更多或更少的資訊報告至不同的目的地。 當您的偵錯工具需求演進時，此方法特別有用。

## <a name="see-also"></a>另請參閱
- [CRT 調試技術](../debugger/crt-debugging-techniques.md)
