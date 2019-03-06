---
title: 報告巨集 |Microsoft Docs
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
ms.openlocfilehash: 2c92424275a1dff69863b81fbf8567fbc4b84499
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689287"
---
# <a name="macros-for-reporting"></a>報告巨集
進行偵錯，您可以使用 **_RPTn**並 **_RPTFn** CRTDBG 中定義的巨集。H，來取代使用`printf`陳述式。 您不需要在 inclose **#ifdef**s，因為它們會自動地消失在您的發行組建 **_DEBUG**未定義。

|巨集|說明|
|-----------|-----------------|
|**_RPT0**、**_RPT1**、**_RPT2**、**_RPT3**、**_RPT4**|輸出訊息字串和零至四個引數。 從 _RPT1 到 **_RPT4**，訊息字串作為引數的 printf 樣式格式字串。|
|**_RPTF0**、**_RPTF1**、**_RPTF2**、**_RPTF4**|與 **_RPTn** 相同，但是這些巨集也會輸出巨集所在位置的檔案名稱和行號。|

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

您可能會發現特定應用程式需要的偵錯報告 C 執行階段程式庫提供的巨集不會提供。 在這些情況下，您可以撰寫專為符合您自己的需求所設計的巨集。 例如，您可以在其中一個標頭檔案中，包含如下的程式碼，來定義名為 **ALERT_IF2** 的巨集：

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

 若要一次呼叫**ALERT_IF2**可以執行的所有函式**printf**程式碼：

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 您可以輕鬆變更自訂的巨集，以增加或減少將資訊報告不同的目的地。 當您偵錯需求不同時，這種方法會特別有用。

## <a name="see-also"></a>請參閱
- [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
