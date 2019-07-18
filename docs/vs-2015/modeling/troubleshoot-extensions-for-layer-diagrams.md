---
title: 針對分層圖擴充功能進行疑難排解 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 38a459760dd66e1160bd8b197ee9883b617639b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439742"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>分層圖擴充功能疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明當您建立圖層模型擴充功能時可能遇到的一些問題。  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>當我按下 F5 偵錯擴充功能時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗執行個體的分層圖上沒有出現我的命令、軌跡處理常式、驗證擴充功能或自訂屬性。  
  
1. 在實驗執行個體中開啟您的擴充方案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，然後在**建置**功能表上，按一下 **重建方案**。  
  
2. 按下**F5**或是**CTRL + F5**來啟動實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 開啟分層圖並測試您的擴充功能。  
  
   如有必要，請繼續執行下一個程序。  
  
#### <a name="an-old-version-of-my-extension-runs"></a>執行的是舊版的擴充功能。  
  
1. 請確定沒有任何 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗執行個體執行中。  
  
2. 刪除下列資料夾： %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache  
  
   > [!NOTE]
   > %Localappdata%通常是*DriveName*: \Users\\*UserName*\AppData\Local。  
  
   如有必要，請繼續執行下一個程序。  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>出現的是舊版的驗證結果，或沒有呼叫我的驗證方法。  
  
1. 在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請在**建置**功能表上，按一下 **清除方案**。 這會清除上一次驗證分析的快取結果。  
  
2. 請確定模型中的圖層與程式碼項目相關聯，而且模型中至少有一個相依性連結。 如果沒有要驗證的項目，就不會叫用驗證。  
  
3. 一般的中斷點可能不會在驗證方法中運作，因為它是在不同的處理序中執行。 如果想要逐步執行您的方法，您必須插入對 `System.Diagnostics.Debugger.Launch()` 的呼叫。  
  
4. 在  **source.extension.vsixmanifest**在圖層驗證專案中，確定您已新增兩者**MEF 元件**項目和**自訂延伸模組類型**項目底下**內容**。  
  
## <a name="see-also"></a>另請參閱  
 [擴充分層圖](../modeling/extend-layer-diagrams.md)
