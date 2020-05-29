---
title: Visual Studio SDK |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67ba3664ee9ea3e349aa4e5e9c01eed04ecddb45
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173561"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可協助您擴充 Visual Studio 功能，或將新功能整合至 Visual Studio。 您可以將擴充功能散發給其他使用者，以及 Visual Studio Marketplace。 下列是一些可擴充 Visual Studio 的方法：

- 將命令、按鈕、功能表和其他 UI 元素新增至 IDE

- 加入工具視窗以取得新功能

- 擴充指定語言的 IntelliSense，或為新的程式設計語言提供 IntelliSense

- 使用 light 燈泡提供提示和建議，協助開發人員撰寫更好的程式碼

- 啟用新語言的支援

- 新增自訂專案類型

- 透過 Visual Studio Marketplace 觸及數百萬名開發人員

  如果您之前從未寫過 Visual Studio 的延伸模組，您應該會發現這些功能的詳細資訊，以及[開始開發 Visual Studio 延伸](../extensibility/starting-to-develop-visual-studio-extensions.md)模組。

## <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE
 Visual Studio SDK 是 Visual Studio 安裝程式中的選用功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="whats-new-in-the-visual-studio-sdk"></a>Visual Studio SDK 的新功能
 Visual Studio SDK 有一些新功能，例如同步自動載入延伸模組警告和 VSIX v3 格式，以及重大變更，這可能會要求您更新延伸模組。 如需詳細資訊，請參閱[Visual Studio 2019 sdk 的新功能](../extensibility/whats-new-visual-studio-2019-sdk.md)和[Visual Studio 2017 Sdk 的新功能](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者經驗指導方針
 在[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中，為您的擴充功能設計 UI，取得絕佳的秘訣。

 您也可以瞭解如何使用[位址 DPI 問題](../extensibility/addressing-dpi-issues2.md)一文，讓您的擴充功能在高 DPI 的裝置上看起來很棒。

 利用[映射服務和目錄](../extensibility/image-service-and-catalog.md)來進行絕佳的影像管理，並支援高 DPI 和主題。

## <a name="find-and-install-existing-visual-studio-extensions"></a>尋找並安裝現有的 Visual Studio 擴充功能
 您可以在 [**工具**] 功能表上的 [**擴充功能和更新**] 對話方塊中找到 Visual Studio 的延伸模組。 如需詳細資訊，請參閱[尋找及使用 Visual Studio 延伸](../ide/finding-and-using-visual-studio-extensions.md)模組。 您也可以在[Visual Studio Marketplace](https://marketplace.visualstudio.com/)中找到擴充功能

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考
 您可以在[VISUAL STUDIO Sdk 參考](../extensibility/visual-studio-sdk-reference.md)中找到 VISUAL STUDIO sdk API 參考。

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例
 您可以在[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中找到 GitHub 上的 VS SDK 擴充功能的開放原始碼範例。 此 GitHub 存放庫包含的範例會說明 Visual Studio 中的各種可擴充功能。

## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源
 如果您對 VSSDK 有任何疑問，或想要分享開發延伸模組的經驗，您可以使用 Visual Studio 擴充性[論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS Gitter 聊天室](https://gitter.im/Microsoft/extendvs)。

 您可以在[VSX Arcana blog](https://blogs.msdn.microsoft.com/vsx/)和 Microsoft mvp 所撰寫的許多 blog 中找到詳細資訊：

- [我的最愛 Visual Studio 延伸模組](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)

- [擴充 Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>另請參閱

- [使用功能表命令建立擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)
- [如何：將擴充性專案遷移至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [常見問題：將增益集轉換成 VSPackage 擴充功能](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [在 managed 程式碼中管理多個執行緒](../extensibility/managing-multiple-threads-in-managed-code.md)
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [將命令新增至工具列](../extensibility/adding-commands-to-toolbars.md)
- [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)
- [編輯器和語言服務延伸模組](../extensibility/editor-and-language-service-extensions.md)
- [擴充專案](../extensibility/extending-projects.md)
- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)
- [建立自訂專案和專案範本](../extensibility/creating-custom-project-and-item-templates.md)
- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [使用和提供服務](../extensibility/using-and-providing-services.md)
- [管理 VSPackages](../extensibility/managing-vspackages.md)
- [Visual Studio 獨立模式 shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [寄送 Visual Studio 延伸模組](../extensibility/shipping-visual-studio-extensions.md)
- [深入探索 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [支援 Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)
