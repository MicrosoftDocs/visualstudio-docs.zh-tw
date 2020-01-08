---
title: 啟用 & 停用 managed 程式碼的完整解決方案分析
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587507"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何：啟用和停用 managed 程式碼的完整解決方案分析

*完整的解決方案分析*表示程式碼分析會檢查C#方案中的所有或 Visual Basic 檔案，不論它們是否已在編輯器中開啟。 根據預設，會*啟用*Visual Basic 的完整解決方案分析，並針對C#*停用*。

查看所有檔案中的所有問題可能會很有用，但也可能會有干擾。 如果您的解決方案非常大或有許多檔案，它會減緩 Visual Studio。 若要限制顯示的問題數目並改善 Visual Studio 效能，您可以停用完整解決方案分析。 如有需要，您可以輕鬆地重新啟用此功能。

在下圖中，已啟用完整解決方案分析。 系統會顯示解決方案中所有檔案中的編譯器和程式碼分析問題，即使它們並未開啟也是一樣。

![已啟用完整解決方案分析。](../code-quality/media/fsa_enabled.png)

下圖顯示在停用完整解決方案分析之後，來自相同解決方案的結果。 只有開啟的方案檔中的編譯器錯誤和程式碼分析問題才會出現在錯誤清單中。

![已停用完整解決方案分析。](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>切換完整解決方案分析

1. 若要開啟 [**選項**] 對話方塊，請在 Visual Studio 的功能表列上，選擇 [**工具**] [ > **選項**]。

1. 在 [**選項**] 對話方塊中，選擇 [**文字編輯器**] > **C#** 或 [**基本**] > [ **Advanced**]。

1. 選取 [**啟用完整解決方案分析**] 核取方塊以啟用完整解決方案分析，或清除方塊來停用它。 當您完成時，請選擇 **[確定]** 。

   ![[啟用完整解決方案分析] 核取方塊。](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>自動停用完整解決方案分析

如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體可供使用，它會自動停用完整解決方案分析（以及其他功能）（如果已啟用）。 如果發生這種情況，則會出現警示，通知您 Visual Studio 已停用某些功能。 按鈕可讓您視需要重新啟用完整的解決方案分析。

![暫停完整解決方案分析的警示文字](../code-quality/media/fsa_alert.png)
