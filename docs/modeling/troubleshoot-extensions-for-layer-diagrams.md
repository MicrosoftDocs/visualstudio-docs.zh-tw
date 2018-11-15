---
title: 針對相依性圖表延伸模組進行疑難排解
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8acde589ebf47d4a67609e847a84bd7c7acd8482
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899639"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>針對相依性圖表延伸模組進行疑難排解

本主題說明當您建立圖層模型擴充功能時可能遇到的一些問題。

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>當我按下 F5 以偵錯 my 擴充性時，我的命令、 軌跡處理常式、 驗證擴充功能或自訂屬性不會出現在 Visual Studio 的實驗執行個體中的相依性圖表

1. Visual Studio 中，並在實驗執行個體中開啟您的擴充方案**建置**功能表上，按一下**重建方案**。

2. 按下**F5**或是**CTRL + F5**啟動 Visual studio 的實驗性執行個體。 開啟 相依性圖表，並測試您的延伸模組。

   如有必要，請繼續執行下一個程序。

## <a name="an-old-version-of-my-extension-runs"></a>執行的是舊版的擴充功能。

1. 請確定 Visual Studio 的實驗執行個體正在執行。

2. 刪除下列資料夾： %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache

   > [!NOTE]
   > %Localappdata%通常是*DriveName*: \Users\\*UserName*\AppData\Local。

   如有必要，請繼續執行下一個程序。

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>出現的是舊版的驗證結果，或沒有呼叫我的驗證方法。

1.  在 Visual Studio 中，實驗執行個體上**建置**功能表上，按一下**清除方案**。 這會清除上一次驗證分析的快取結果。

2.  請確定模型中的圖層與程式碼項目相關聯，而且模型中至少有一個相依性連結。 如果沒有要驗證的項目，就不會叫用驗證。

3.  一般的中斷點可能不會在驗證方法中運作，因為它是在不同的處理序中執行。 如果想要逐步執行您的方法，您必須插入對 `System.Diagnostics.Debugger.Launch()` 的呼叫。

4.  在  **source.extension.vsixmanifest**在圖層驗證專案中，確定您已新增兩者**MEF 元件**項目和**自訂延伸模組類型**項目底下**內容**。

## <a name="see-also"></a>另請參閱

- [擴充相依性圖表](../modeling/extend-layer-diagrams.md)
