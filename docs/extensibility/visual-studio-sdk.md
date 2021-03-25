---
title: Visual Studio SDK |Microsoft Docs
description: Visual Studio SDK 可協助您擴充功能，或將新功能新增至 Visual Studio。 瞭解您可以擴充 Visual Studio 的一些方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91411ec183e6c51abd825af1080c4330ca46fc90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062521"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可協助您擴充 Visual Studio 功能，或將新功能整合到 Visual Studio。 您可以將延伸模組散發給其他使用者以及 Visual Studio Marketplace。 下列是一些可擴充 Visual Studio 的方法：

- 將命令、按鈕、功能表和其他 UI 元素新增至 IDE

- 加入新功能的工具視窗

- 針對指定的語言擴充 IntelliSense，或為新的程式設計語言提供 IntelliSense

- 使用 light 燈泡來提供提示和建議，以協助開發人員撰寫更好的程式碼

- 啟用新語言的支援

- 新增自訂專案類型

- 透過 Visual Studio Marketplace 觸及上百萬位開發人員

  如果您之前從未撰寫過 Visual Studio 的延伸模組，您應該會找到這些功能的詳細資訊，以及 [開始開發 Visual Studio 擴充](../extensibility/starting-to-develop-visual-studio-extensions.md)功能的相關資訊。

## <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE
 Visual Studio SDK 是 Visual Studio 安裝程式中的選擇性功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="whats-new-in-the-visual-studio-sdk"></a>Visual Studio SDK 的新功能
 Visual Studio SDK 有一些新功能，例如同步自動載入延伸模組警告和 VSIX v3 格式以及中斷變更，您可能需要更新擴充功能。 如需詳細資訊，請參閱 [Visual Studio 2019 sdk 的新功能](../extensibility/whats-new-visual-studio-2019-sdk.md) 和 [Visual Studio 2017 Sdk 的新功能](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者經驗指導方針
 取得在 [Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中，為您的擴充功能設計 UI 的絕佳秘訣。

 您也可以瞭解如何使用「 [位址 DPI 問題](../extensibility/addressing-dpi-issues2.md) 」一文，讓您的延伸模組在高 DPI 裝置上看起來很棒。

 利用 [映射服務和目錄](../extensibility/image-service-and-catalog.md) 來提供絕佳的影像管理，以及高 DPI 和主題的支援。

## <a name="find-and-install-existing-visual-studio-extensions"></a>尋找並安裝現有的 Visual Studio 擴充功能
 您可以在 [**工具**] 功能表上的 [**擴充功能和更新**] 對話方塊中找到 Visual Studio 延伸模組。 如需詳細資訊，請參閱 [尋找和使用 Visual Studio 擴充](../ide/finding-and-using-visual-studio-extensions.md)功能。 您也可以在[Visual Studio Marketplace](https://marketplace.visualstudio.com/)中找到擴充功能

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考
 您可以在 [VISUAL STUDIO Sdk 參考](../extensibility/visual-studio-sdk-reference.md)中找到 VISUAL STUDIO sdk API 參考。

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例
 您可以在 GitHub 的 [Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中找到 VS SDK 擴充功能的開放原始碼範例。 此 GitHub 存放庫包含的範例會說明 Visual Studio 中的各種可擴充功能。

## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源
 如果您對 VSSDK 有任何疑問，或想要分享開發延伸模組的體驗，您可以使用 Visual Studio 擴充性 [論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) 或 [ExtendVS Gitter 聊天室](https://gitter.im/Microsoft/extendvs)。

 您可以在 [VSX Arcana blog](/archive/blogs/vsx/) 中找到更多的資訊，以及 Microsoft mvp 所撰寫的許多 blog：

- [我的最愛 Visual Studio 擴充功能](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)

- [擴充 Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>另請參閱

- [使用功能表命令建立擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)
- [如何：將擴充性專案遷移至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [常見問題：將增益集轉換成 VSPackage 擴充功能](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [在 managed 程式碼中管理多個執行緒](../extensibility/managing-multiple-threads-in-managed-code.md)
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [將命令新增至工具列](../extensibility/adding-commands-to-toolbars.md)
- [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)
- [編輯器和語言服務延伸模組](../extensibility/editor-and-language-service-extensions.md)
- [擴充專案](../extensibility/extending-projects.md)
- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)
- [建立自訂專案和專案範本](../extensibility/creating-custom-project-and-item-templates.md)
- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
- [延伸 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [使用和提供服務](../extensibility/using-and-providing-services.md)
- [管理 VSPackages](../extensibility/managing-vspackages.md)
- [Visual Studio 獨立模式 shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [寄送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
- [深入探索 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [支援 Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)