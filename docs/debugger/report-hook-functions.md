---
title: 報表攔截函式 |Microsoft Docs
description: 請參閱 Visual Studio 中的報表攔截函式。 報告攔截函式，使用 _CrtSetReportHook 安裝，會在每次 _CrtDbgReport 產生偵錯報告時呼叫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dea558d2f125c1e64f46bb4fbf738434eda2394
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205615"
---
# <a name="report-hook-functions"></a>報告攔截函式
報告攔截函式，使用 [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook) 安裝，會在每次 [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) 產生偵錯報告時呼叫。 除此之外，您可以使用它來篩選報告以專注於特定類型的配置。 報告攔截函式應該有像下列的原型：

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 您傳遞給 **_CrtSetReportHook** 的指標是 **_CRT_REPORT_HOOK** 類型，如 crtdbg.h 裡中所定義。H：

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 當執行階段程式庫呼叫攔截函式時，*nRptType* 引數包含報告的分類 (**_CRT_WARN**、**_CRT_ERROR** 或 **_CRT_ASSERT**)，*szMsg* 包含完整重組報告訊息字串的指標，而 *retVal* 指定 `_CrtDbgReport` 是否應該在產生報告或啟動偵錯工具繼續照常執行。 (*retVal* 值為零時會繼續執行，值為 1 時會啟動偵錯工具。)

 如果攔截能完整處理該訊息，而不需要進一步的報告，應該就會傳回 **TRUE**。 如果傳回 **FALSE**， `_CrtDbgReport` 就會正常回報訊息。

## <a name="see-also"></a>請參閱
- [調試攔截函式寫入](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
