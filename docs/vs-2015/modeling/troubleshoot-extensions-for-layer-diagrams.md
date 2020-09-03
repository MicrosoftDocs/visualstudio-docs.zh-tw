---
title: 疑難排解分層圖的延伸模組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658481"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>分層圖擴充功能疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明當您建立圖層模型擴充功能時可能遇到的一些問題。

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-vsprvs"></a>當我按下 F5 偵錯擴充功能時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗執行個體的分層圖上沒有出現我的命令、軌跡處理常式、驗證擴充功能或自訂屬性。

1. 在的實驗實例中開啟您的擴充方案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，然後在 [ **組建** ] 功能表上，按一下 [ **重建方案**]。

2. 按 **f5** 或 **CTRL + F5** 啟動的實驗實例 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 開啟分層圖並測試您的擴充功能。

   如有必要，請繼續執行下一個程序。

#### <a name="an-old-version-of-my-extension-runs"></a>執行的是舊版的擴充功能。

1. 請確定沒有任何 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗執行個體執行中。

2. 刪除下列資料夾：%LocalAppData%\Microsoft\VisualStudio \\ [version] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% 通常是*DriveName*： \Users \\ *UserName*\AppData\Local。

   如有必要，請繼續執行下一個程序。

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>出現的是舊版的驗證結果，或沒有呼叫我的驗證方法。

1. 在的實驗實例中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，按一下 [ **建立** ] 功能表上的 [ **清除方案**]。 這會清除上一次驗證分析的快取結果。

2. 請確定模型中的圖層與程式碼項目相關聯，而且模型中至少有一個相依性連結。 如果沒有要驗證的項目，就不會叫用驗證。

3. 一般的中斷點可能不會在驗證方法中運作，因為它是在不同的處理序中執行。 如果想要逐步執行您的方法，您必須插入對 `System.Diagnostics.Debugger.Launch()` 的呼叫。

4. 在圖層驗證專案的**extension.vsixmanifest**中，確定您已在 [**內容**] 底下加入**MEF 元件**專案和**自訂延伸模組類型**專案。

## <a name="see-also"></a>另請參閱
 [擴充分層圖](../modeling/extend-layer-diagrams.md)
