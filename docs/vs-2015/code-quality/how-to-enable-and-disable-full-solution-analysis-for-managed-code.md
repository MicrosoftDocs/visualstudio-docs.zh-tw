---
title: 如何：啟用和停用 Managed 程式碼的完整解決方案分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646284"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何：啟用和停用 Managed 程式碼的完整解決方案分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 本主題僅適用于 Visual Studio 2015 Update 3 RC 和更新版本。

 *完整的解決方案分析*是一項 Visual Studio 的功能，可讓您選擇只在開啟的視覺效果C#或在您的方案中 Visual Basic 檔案中看到程式碼分析問題， C#或是在您的中開啟和關閉的視覺效果或 Visual Basic 檔案解.

 雖然能夠查看所有檔案中的所有問題都很有用，但如果您的解決方案非常大或有許多檔案，可能會造成混亂，甚至會變慢 Visual Studio。  若要限制顯示的問題數目並改善 Visual Studio 效能，您可以停用完整解決方案分析。 如有需要，您可以輕鬆地重新啟用這項功能。

#### <a name="to-toggle-full-solution-analysis"></a>若要切換完整的解決方案分析

1. 在 Visual Studio 的主功能表上，選擇 [**工具** &#124; ] [**選項**] 以查看 [**選項**] 對話方塊。

2. 在 [**選項**] 對話方塊中，選擇 [**文字編輯器** &#124; **C#** ] 或 [**基本** &#124; ] [ **Advanced**]。

3. 選取 [**啟用完整解決方案分析**] 核取方塊以啟用完整解決方案分析，或清除方塊來停用它。 當您完成時，請選擇 [**確定]** 按鈕。

     ![[啟用完整解決方案分析] 核取方塊。](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>啟用和停用完整解決方案分析的結果
 在下列螢幕擷取畫面中，您可以在啟用完整解決方案分析時看到結果。 無論檔案是否開啟，解決方案中*所有*檔案中的所有錯誤和程式碼分析問題都會出現。

 ![已啟用完整解決方案分析。](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 下列螢幕擷取畫面顯示在停用完整解決方案分析之後，來自相同解決方案的結果。 只有開啟的方案檔中的錯誤和程式碼分析問題才會出現在錯誤清單中。

 ![已停用完整解決方案分析。](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>自動停用完整解決方案分析
 如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體可供使用，它會自動停用完整解決方案分析（以及其他功能）（如果已啟用）。 如果發生這種情況，則會出現警示通知您。 如果您想要這樣做，按鈕可讓您重新啟用完整的解決方案分析。

 ![暫停完整解決方案分析的警示文字](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>其他詳細資料
 根據預設，會啟用 Visual Basic 的完整解決方案分析，並針對視覺C#效果停用。

 Visual Studio Update 3 RC 包含增強的程式碼分析器診斷 v2 引擎，可大幅減少記憶體使用量並將 CPU 時間減少到閒置，即使已啟用完整的解決方案分析。
