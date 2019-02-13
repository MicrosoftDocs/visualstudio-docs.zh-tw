---
title: Visual C/c + + 自訂視覺化檢視相容性
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
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: a51f2d87b432bf6f4a3925b55622273b56cf5c32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920960"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/c + + 自訂視覺化檢視相容性

從 Visual Studio 2019，Visual c + + 包含用於裝載需要大量記憶體的元件使用外部的 64 位元處理序已改善偵錯工具。 一部分此更新的詳細資訊，您必須更新特定 Visual C/c + + 運算式評估工具的延伸模組，才能讓它們相容於新的偵錯工具。

如果您目前使用舊版的 C/c + + EE 增益集或 C/c + + 自訂視覺化檢視，您可以關閉這個外部處理序的使用量前往**工具** > **選項** >  **偵錯**，然後取消選取並**負載偵錯符號在外部處理序 （僅限機器碼）**。 如果您取消選取此選項，會發生在 IDE (devenv.exe) 程序中的記憶體使用量大幅增加。 因此，如果您要偵錯大型專案時，建議您先使用延伸模組的擁有者，讓它與此偵錯選項相容。

如果您是舊版的 C/c + + EE 增益集或 C/c + + 自訂視覺化檢視的擁有者，您可以找到闔家上載入您的背景工作處理序中的延伸模組的詳細資訊[Concord 擴充性範例 wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)。 您也可以找到[C/c + + 自訂視覺化檢視範例](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)。