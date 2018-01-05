---
title: "如何： 啟用和停用 Managed 程式碼的完整解決方案分析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: dotnet
ms.openlocfilehash: eb69b6c2e26aab36ec4dac0a664cb20b411a815a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>如何： 啟用和停用 Managed 程式碼的完整解決方案分析
> [!NOTE]
>  本主題只適用於 Visual Studio 2015 Update 3 RC 和更新版本。  
  
 *完整解決方案分析*是一種 Visual Studio 功能，可讓您選擇是否您查看程式碼分析問題，只在開啟 Visual C# 或 Visual Basic 檔案在您的方案，或開啟或關閉 Visual C# 或 Visual Basic 方案中的檔案。  
  
 雖然能看到所有的檔案中的所有問題很有用，它可以是分散注意力，而且即使慢 Visual Studio 如果您的解決方案非常大，或具有許多檔案。  若要限制顯示的問題數目，並改善 Visual Studio 效能，您可以停用完整解決方案分析。 如果您想要輕鬆地重新啟用這項功能。  
  
#### <a name="to-toggle-full-solution-analysis"></a>若要切換完整解決方案分析  
  
1.  在 Visual studio 主功能表上選擇 [**工具**&#124;**選項**檢視**選項**] 對話方塊。  
  
2.  在**選項**對話方塊方塊中，選擇**文字編輯器**&#124;**C#**或**基本**&#124;**進階**。  
  
3.  選取**啟用完整解決方案分析**核取方塊以啟用完整解決方案分析，或清除此方塊可停用它。 選擇**確定**按鈕瀏覽完畢時。  
  
     ![啟用完整解決方案分析核取方塊。] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>啟用和停用完整解決方案分析的結果  
 在下列螢幕擷取畫面中，您可以看到結果時已啟用完整解決方案分析。 所有錯誤和中的程式碼分析問題*所有*的方案中的檔案會出現，無論檔案是否為開啟。  
  
 ![啟用完整解決方案分析。] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 下列螢幕擷取畫面顯示從相同的方案結果之後停用完整解決方案分析。 只將錯誤和中的程式碼分析問題開啟的方案檔案會出現在 錯誤清單。  
  
 ![停用的完整解決方案分析。] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>自動停用完整解決方案分析  
 如果 Visual Studio 偵測到 200 MB 或更少的系統記憶體可供其使用，它會自動停用完整解決方案分析 （以及一些其他功能） 如果已啟用。 如果發生這種情況，會出現警示，通知您這個。 按鈕可讓您重新啟用完整解決方案分析，如果您想要執行這項操作。  
  
 ![警示文字中暫停完整解決方案分析](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>其他詳細資料  
 根據預設，會完整解決方案分析 Visual basic 中啟用，而且停用 Visual C#。  
  
 Visual Studio Update 3 RC 包含增強的程式碼分析師診斷 v2 引擎的大幅降低記憶體使用量，並減少 CPU 時間與閒置，即使已啟用完整解決方案分析。