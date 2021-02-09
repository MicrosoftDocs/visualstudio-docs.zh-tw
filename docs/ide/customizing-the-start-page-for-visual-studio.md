---
title: 變更啟動體驗
description: 瞭解如何自訂您的啟動體驗，讓 Visual Studio 使用最適合您的工具開啟。
ms.custom: SEO-VS-2020
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 855218fb6ff2e90cb06e0f48695b64c75e7036b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886583"
---
# <a name="customize-startup"></a>自訂啟動

您可以使用幾種不同的方式 (例如，開啟最新解決方案或只開啟空的開發環境) 來自訂 Visual Studio 的啟動體驗。

::: moniker range="vs-2017"

您也可以顯示自訂起始頁，這是一個在工具視窗中執行的 Windows Presentation Foundation (WPF) XAML 頁面，並且可以執行 Visual Studio 的內部命令。

::: moniker-end

## <a name="to-change-the-startup-item"></a>變更啟動項目

1. 在功能表列上，選擇 [**工具**  >  **選項**]。

2. 展開 [環境]，然後選擇 [啟動]。

::: moniker range="vs-2017"

3. 在 [啟動時] 清單中，選擇在 Visual Studio 啟動之後要顯示的項目。

::: moniker-end

::: moniker range=">=vs-2019"

3. 在 [啟動時] 中開啟清單，選擇您想要在 Visual Studio 啟動後發生的狀況。 您可以從 [開始視窗] (這可讓您開啟新或現有的專案)、[最新的解決方案] 或 [空白環境] 中選擇。

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>顯示自訂起始頁

您可以使用 Visual Studio SDK [建立您自己的自訂起始頁](../extensibility/creating-a-custom-start-page.md)，或使用其他人已經建立的自訂起始頁。 例如，您可以在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads) \(英文\) 找到自訂起始頁。

若要安裝自訂起始頁，請開啟 .vsix 檔案，或複製起始頁檔案並貼到電腦上的 *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* 資料夾中。

### <a name="to-select-which-custom-start-page-to-display"></a>選取要顯示的自訂起始頁

1. 在功能表列上選擇 [工具]**[選項]** > 。

1. 展開 [環境]，然後選擇 [啟動]。

1. 在 [自訂起始頁] 清單中，選擇您要的頁面。

> [!TIP]
> 如果自訂起始頁中的錯誤導致 Visual Studio 當機，請以安全模式開啟 Visual Studio，然後將它設定為使用預設起始頁。 請參閱 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。

## <a name="see-also"></a>另請參閱

- [將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
