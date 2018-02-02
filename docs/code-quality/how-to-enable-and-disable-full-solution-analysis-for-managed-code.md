---
title: "如何： 啟用和停用 Managed 程式碼的完整解決方案分析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何： 啟用和停用 managed 程式碼的完整解決方案分析

*完整解決方案分析*是 Visual Studio 功能，可讓您查看程式碼分析問題，只在方案中開啟的 Visual C# 或 Visual Basic 檔案也在程式碼中的檔案或已關閉。 根據預設，會完整解決方案分析 Visual basic 中啟用，而且停用 Visual C#。

雖然能看到所有的檔案中的所有問題很有用，它可以是令人分心。 它也可以緩慢的 Visual Studio 關閉如果您的方案非常大，或有很多檔案。 若要限制顯示的問題數目，並改善 Visual Studio 效能，您可以停用完整解決方案分析。 必要時您可以輕鬆地重新啟用這項功能。

## <a name="to-toggle-full-solution-analysis"></a>若要切換完整解決方案分析

1. 若要開啟**選項**對話方塊中，Visual Studio 中的功能表列上選擇**工具** > **選項**。

1. 在**選項**對話方塊方塊中，選擇**文字編輯器** > **C#**或**基本** >  **進階**。

1. 選取**啟用完整解決方案分析**核取方塊以啟用完整解決方案分析，或清除此方塊可停用它。 選擇**確定**按鈕瀏覽完畢時。

    ![啟用完整解決方案分析核取方塊。] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>啟用和停用完整解決方案分析的結果

在下列螢幕擷取畫面中，您可以看到結果時已啟用完整解決方案分析。 所有錯誤和中的程式碼分析問題*所有*的方案中的檔案會出現，無論檔案是否為開啟。

![啟用完整解決方案分析。] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

下列螢幕擷取畫面顯示從相同的方案結果之後停用完整解決方案分析。 只將錯誤和中的程式碼分析問題開啟的方案檔案會出現在 錯誤清單。

![停用的完整解決方案分析。] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>自動停用完整解決方案分析

如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體可供其使用，它會自動停用完整解決方案分析 （以及一些其他功能） 如果已啟用。 如果發生這種情況，會出現警示，通知您這個。 按鈕可讓您視需要重新啟用完整解決方案分析。

![警示文字中暫停完整解決方案分析](../code-quality/media/fsa_alert.png "FSA_Alert")