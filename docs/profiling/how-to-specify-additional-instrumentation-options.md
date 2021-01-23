---
title: 指定其他的檢測選項 | Microsoft Docs
description: 瞭解如何使用 Visual Studio IDE 或使用命令列工具來檢測二進位檔。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aaa6a222ca320ff9e8e3d117c2218e170d67d683
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721849"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>如何：指定其他的檢測選項

您可以使用 Visual Studio IDE 或使用命令列工具來檢測二進位檔。 如果是從 IDE 中檢測二進位檔，您可以為 [VSInstr](../profiling/vsinstr.md) 工具指定其他的檢測選項，藉以控制檢測期間所收集的資料量。 這些選項可以在工作階段或目標層級中使用。 例如，若要在檢測程序期間包含或排除特定函式，請在目標層級使用其他的檢測選項。

> [!IMPORTANT]
> 插入的每個探查會稍微改變原始程式的行為。 這個改變會在分析階段造成額外負荷。 即使扣除掉這個額外負荷的近似值，它仍會對多執行緒的應用程式有輕微的執行時間變化。 [VSInstr](../profiling/vsinstr.md) 工具選項可協助在程式碼剖析期間控制資料的收集。

## <a name="to-specify-additional-instrumentation-option"></a>指定其他的檢測選項

1. 在 [效能總管] 中，選取 [效能工作階段]，然後以滑鼠右鍵按一下並選取 [屬性]。

2. 在 [屬性頁] 中，按一下 [進階] 屬性。

3. 在 [其他檢測選項] 方塊中輸入選項。

     例如，使用 /CONTROL:THREAD 以指定程式碼剖析層級。 如需選項的完整清單，請參閱 [VSInstr](../profiling/vsinstr.md)。

4. 按一下 [確定]。

## <a name="see-also"></a>另請參閱

[設定效能會話](../profiling/configuring-performance-sessions.md) 
[從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)
