---
title: 啟用&禁用託管代碼的完整解決方案分析
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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428268"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何：為託管代碼啟用和禁用完整的解決方案分析

*完整的解決方案分析*意味著代碼分析會檢查解決方案中的所有 C# 或 Visual Basic 檔，無論這些檔是否在編輯器中打開。 預設情況下，為 Visual Basic*啟用*了完整的解決方案分析，並且*禁用*了 C#。

查看所有檔中的所有問題都很有用，但也可能會分散注意力。 如果解決方案非常大或有許多檔，它會減慢 Visual Studio 的速度。 要限制顯示的問題數量並提高 Visual Studio 的性能，可以禁用完整的解決方案分析。 如有必要，可以輕鬆地重新啟用此功能。

在下圖中，啟用了完整的解決方案分析。 將顯示解決方案中的所有檔中的編譯器和代碼分析問題，即使它們未打開也是如此。

![已啟用完整的解決方案分析。](../code-quality/media/fsa_enabled.png)

下圖顯示了禁用完整解決方案分析後同一解決方案的結果。 在"錯誤清單"中，只有打開的解決方案檔中的編譯器錯誤和代碼分析問題才會顯示。

![禁用了完整的解決方案分析。](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>切換完整解決方案分析

1. 要打開"**選項"** 對話方塊，在視覺化工作室的功能表列上選擇 **"工具** > **選項**"。

1. 在"**選項**"對話方塊中，**選擇文字編輯器** > **C#** 或**基本** > **高級**。

1. 選擇"**啟用完整解決方案分析**"核取方塊以啟用完整的解決方案分析，或清除該框以禁用該框。 完成後選擇 **"確定**"。

   ![啟用完整的解決方案分析核取方塊。](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>自動禁用完整的解決方案分析

如果 Visual Studio 檢測到其可以使用 200 MB 或更少的系統記憶體，則如果啟用了完整解決方案分析（以及某些其他功能），它將自動禁用它。 如果發生這種情況，將顯示一個警報，通知您 Visual Studio 已禁用某些功能。 通過按鈕，您可以重新啟用完整的解決方案分析（如果需要）。

![警報文本暫停完整的解決方案分析](../code-quality/media/fsa_alert.png)
