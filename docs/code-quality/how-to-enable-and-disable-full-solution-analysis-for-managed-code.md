---
title: HOW TO：啟用和停用 Managed 程式碼的完整解決方案分析
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- dotnet
ms.openlocfilehash: ffda04828789a591c0e6dca35ef391fe6b8556d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035467"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>HOW TO：啟用和停用 managed 程式碼的完整解決方案分析

*完整解決方案分析*是一種 Visual Studio 功能，可讓您查看程式碼分析問題，只在開啟的視覺效果C#或 Visual Basic 檔案中您的方案，或已關閉的程式碼檔案中。 根據預設，會完整解決方案分析*啟用*Visual basic 中，並*停用*視覺效果C#。

它可用來查看所有的檔案中的所有問題，但它也是令人分心。 向下中，如果您的解決方案非常大或有許多檔案，它會減緩 Visual Studio。 若要限制顯示的問題數目，並改善 Visual Studio 效能，您可以停用完整解決方案分析。 必要時您可以輕鬆地重新啟用這項功能。

## <a name="to-toggle-full-solution-analysis"></a>若要切換完整解決方案分析

1. 若要開啟 **選項**對話方塊中，在 Visual Studio 功能表列上的選擇**工具** > **選項**。

1. 在 **選項**對話方塊方塊中，選擇**文字編輯器** >  **C#** 或是**基本** >  **進階**。

1. 選取 **啟用完整解決方案分析**核取方塊以啟用完整解決方案分析，或清除此方塊可停用它。 選擇**確定**完成時。

    ![啟用完整解決方案分析 核取方塊。](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>啟用和停用完整解決方案分析的結果

在下列螢幕擷取畫面中，您可以看到結果時已啟用完整解決方案分析。 所有錯誤和中的程式碼分析問題*所有*的方案中的檔案會出現，無論檔案是否為開啟。

![啟用完整解決方案分析。](../code-quality/media/fsa_enabled.png)

下列螢幕擷取畫面會顯示相同的方案的結果之後停用完整解決方案分析。 只有 「 錯誤 」 和 「 程式碼分析問題，在開啟的方案檔中會出現在**錯誤清單**。

![停用完整解決方案分析。](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>自動停用完整解決方案分析

如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體提供給它，它會自動停用完整解決方案分析 （和一些其他功能） 如果已啟用。 如果發生這種情況，會出現警示，通知您，Visual Studio 已停用某些功能。 按鈕可讓您重新啟用完整解決方案分析，如果您想要。

![警示文字中暫停完整解決方案分析](../code-quality/media/fsa_alert.png)