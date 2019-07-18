---
title: Visual C /C++自訂視覺化檢視相容性
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901162"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C /C++自訂視覺化檢視相容性

從 Visual Studio 2019，視覺效果C++包括用於裝載需要大量記憶體的元件使用外部的 64 位元處理序已改善偵錯工具。 做為一部分此更新中，特定的延伸模組，Visual c /C++運算式評估工具必須更新以使其與新的偵錯工具相容。

如果您目前使用舊版的 C /C++ EE 增益集或 C /C++自訂視覺化檢視，您可以關閉此外部程序的使用方式經由**工具** > **選項** > **偵錯**，然後取消選取並**載入偵錯符號在外部處理序 （僅限機器碼）**。 如果您取消選取此選項，會發生在 IDE (devenv.exe) 程序中的記憶體使用量大幅增加。 因此，如果您要偵錯大型專案時，建議您先使用延伸模組的擁有者，讓它與此偵錯選項相容。

如果您所擁有的舊版 C /C++ EE 增益集或 C /C++自訂視覺化檢視，您可以找到闔家上載入您的背景工作處理序中的延伸模組的詳細資訊[Concord 擴充性範例 wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)。 您也可以找到[C /C++自訂視覺化檢視範例](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)。