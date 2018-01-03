---
title: "在 Visual Studio 中安裝自訂起始頁或變更起始項目 | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6bf05e014ff70b221d1ec77c4ee5677764142ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>自訂 Visual Studio 的起始頁

您可以透過幾種不同的方式來自訂 Visual Studio 的起始體驗，例如顯示 [開啟專案] 對話方塊或開啟最近載入的方案。 您也可以顯示自訂起始頁，這是一個在工具視窗中執行的 Windows Presentation Foundation (WPF) XAML 頁面，並且可以執行 Visual Studio 的內部命令。

## <a name="to-change-the-startup-item"></a>變更啟動項目

1. 在功能表列上選擇 [工具] 、[選項] 。

1. 展開 [環境]，然後選擇 [啟動]。

1. 在 [啟動時] 清單中，選擇在 Visual Studio 啟動之後要顯示的項目。

## <a name="to-show-a-custom-start-page"></a>顯示自訂起始頁

您可以使用 Visual Studio SDK [建立您自己的自訂起始頁](../extensibility/creating-a-custom-start-page.md)，或使用其他人已經建立的自訂起始頁。 例如，您可以在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads) \(英文\) 找到自訂起始頁。

若要安裝自訂起始頁，請開啟 .vsix 檔案，或複製起始頁檔案並貼到電腦上的 **%USERPROFILE%\Documents\Visual Studio 2017\StartPages** 資料夾中。

### <a name="to-select-which-custom-start-page-to-display"></a>選取要顯示的自訂起始頁

1. 在功能表列上選擇 [工具] 、[選項] 。

1. 展開 [環境]，然後選擇 [啟動]。

1. 在 [自訂起始頁] 清單中，選擇您要的頁面。

> [!NOTE]
> 如果自訂起始頁中的錯誤導致 Visual Studio 當掉，請以安全模式啟動 Visual Studio，然後設定它使用預設起始頁。 請參閱 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。

## <a name="see-also"></a>另請參閱

[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)
