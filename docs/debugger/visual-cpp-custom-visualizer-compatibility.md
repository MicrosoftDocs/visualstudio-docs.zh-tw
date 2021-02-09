---
title: Visual C/c + + 自訂視覺化檢視相容性
description: Visual Studio 2019 中的新功能可能與舊版 C/c + + 運算式評估工具增益集和自訂視覺化者不相容。 如需詳細資訊，請參閱本文。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32ad6b4b699f9cfe02739f341a4f9ddf29360f37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884308"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/c + + 自訂視覺化檢視相容性

從 Visual Studio 2019 開始，c + + 包含改良的偵錯工具，該偵錯工具會使用外部64位進程來裝載其記憶體密集型元件。 在這項更新中，必須更新 C/c + + 運算式評估工具的某些延伸模組，使其與新的偵錯工具相容。

如果您目前使用的是舊版 C/c + + EE 增益集或 C/c + + 自訂視覺化，您可以前往 [**工具** 選項] 偵錯工具來關閉此外部進程的使用方式  >    >  ****，然後 **在外部進程中取消核取 [載入偵錯工具符號] (僅限原生)**。 如果您取消選取此選項，將會發生 IDE 內記憶體使用量大幅增加 ( # A0) 進程。 因此，如果您想要對大型專案進行 debug 錯，建議您與延伸模組的擁有者合作，使其與這個偵錯工具選項相容。

如果您是舊版 C/c + + EE 增益集或 C/c + + 自訂視覺化程式的擁有者，您可以在 Concord 擴充性 [範例 wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)上，找到有關選擇在背景工作進程中載入擴充功能的詳細資訊。 您也可以找到 [C/c + + 自訂視覺化檢視範例](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)。