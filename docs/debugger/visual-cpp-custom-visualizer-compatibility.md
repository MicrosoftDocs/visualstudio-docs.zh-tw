---
title: Visual C/C++自訂視覺化檢視相容性
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430626"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++自訂視覺化檢視相容性

從 Visual Studio 2019 開始， C++包含改良的偵錯工具，它會使用外部64位進程來裝載其記憶體密集型元件。 在此更新中，必須更新 C/C++ expression 評估工具的某些延伸模組，使其與新的偵錯工具相容。

如果您目前使用的是舊版 C/C++ EE 載入器或 CC++ /自訂視覺化檢視，您可以前往 [**工具**]  > **選項** >  的**調試**程式，然後取消選擇 [載入] [debug]，關閉此外部進程的使用方式。 **外部進程中的符號（僅限原生）** 。 如果您取消選取此選項，將會在 IDE （devenv）程式內大幅增加記憶體使用量。 因此，如果您預期會進行大型專案的偵錯工具，建議您與延伸模組的擁有者合作，使其與此偵錯工具選項相容。

如果您是舊版 C/C++ EE 載入器或 C/C++自訂視覺化程式的擁有者，您可以在 Concord 擴充性[範例 wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)（英文）中找到有關選擇在背景工作進程中載入擴充功能的詳細資訊。 您也可以尋找[C/C++自訂視覺化檢視範例](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)。