---
title: 如何： 啟用和停用 Managed 程式碼的完整解決方案分析 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4815963966c54d7c237737d85c2e573e886bc9ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489656"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何： 啟用和停用 Managed 程式碼的完整解決方案分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 啟用和停用完整解決方案分析 Managed 程式碼](https://docs.microsoft.com/visualstudio/code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code)。  
  
附註]
>  本主題只適用於 Visual Studio 2015 Update 3 RC 和更新版本。  
  
 *完整解決方案分析*是一種 Visual Studio 功能，可讓您選擇您是否看到只在開啟 Visual C# 或 Visual Basic 檔案在您的方案，或開啟和關閉 Visual C# 或 Visual Basic 檔案中您方案中的程式碼分析問題。  
  
 雖然能夠查看所有檔案中的所有問題非常有用，它可能會分散注意力，而且即使慢 Visual Studio，如果您的解決方案非常大或有很多檔案。  若要限制顯示的問題數目，並改善 Visual Studio 效能，您可以停用完整解決方案分析。 如果您想要輕鬆地重新啟用這項功能。  
  
#### <a name="to-toggle-full-solution-analysis"></a>若要切換完整解決方案分析  
  
1.  在 在 Visual Studio 主功能表中，選擇**工具** &#124; **選項**檢視**選項**對話方塊。  
  
2.  在 **選項**對話方塊方塊中，選擇**文字編輯器** &#124; **C#** 或**基本** &#124; **進階**.  
  
3.  選取 **啟用完整解決方案分析**核取方塊以啟用完整解決方案分析，或清除此方塊可停用它。 選擇**確定**按鈕，當您完成時。  
  
     ![啟用完整解決方案分析 核取方塊。](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>啟用和停用完整解決方案分析的結果  
 在下列螢幕擷取畫面中，您可以看到結果時已啟用完整解決方案分析。 所有錯誤和中的程式碼分析問題*所有*的方案中的檔案會出現，無論檔案是否為開啟。  
  
 ![啟用完整解決方案分析。](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 下列螢幕擷取畫面會顯示相同的方案的結果之後停用完整解決方案分析。 只有 「 錯誤 」 和 「 程式碼分析問題，在開啟的方案檔會出現在 錯誤清單。  
  
 ![停用完整解決方案分析。](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>自動停用完整解決方案分析  
 如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體提供給它，它會自動停用完整解決方案分析 （以及一些其他功能） 如果已啟用。 如果發生這種情況，會出現通知，告知您這個。 按鈕可讓您重新啟用完整解決方案分析，如果您想要執行這項操作。  
  
 ![警示文字中暫停完整解決方案分析](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>其他詳細資料  
 根據預設，是針對 Visual Basic 啟用完整解決方案分析，並將其停用 Visual C# 中。  
  
 Visual Studio Update 3 RC 包含增強的程式碼分析師診斷 v2 引擎，大幅降低記憶體使用量，並減少 CPU 時間閒置，即使已啟用完整解決方案分析。



