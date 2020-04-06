---
title: 視覺工作室 SDK |微軟文件
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
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698068"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可説明您擴展視覺工作室功能或將新功能集成到可視化工作室中。 您可以將擴展分發給其他使用者以及可視化工作室應用商店。 下列是一些可擴充 Visual Studio 的方法：

- 將指令、按鈕、選單和其他 UI 元素加入 IDE

- 新增功能加入工具視窗

- 延伸給定語言的 IntelliSense,或為新程式設計語言提供 IntelliSense

- 使用燈泡提供提示和建議,幫助開發人員編寫更好的代碼

- 開啟對新語言的支援

- 新增自訂項目型態

- 通過可視化工作室市場覆蓋數百萬開發人員

  如果您以前從未編寫過 Visual Studio 延伸,您應該找到有關這些功能的更多資訊,並在[開始開發 Visual Studio 擴充](../extensibility/starting-to-develop-visual-studio-extensions.md)。

## <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE
 可視化工作室 SDK 是可視化工作室設置中的可選功能。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>視覺工作室 2017 SDK 中的新增功能
 Visual Studio SDK 具有一些新功能,如 VSIX v3 格式以及重大更改,這可能需要您更新擴展。 有關詳細資訊,請參閱[Visual Studio 2017 SDK 中的新增功能](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。

## <a name="visual-studio-user-experience-guidelines"></a>視覺化工作室使用者體驗指南
 在[Visual Studio 用戶體驗指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中獲取為擴展設計 UI 的提示。

 您還可以瞭解如何透過[「位址 DPI 問題](../extensibility/addressing-dpi-issues2.md)」一文在高 DPI 裝置上使擴展看起來很棒。

 利用[圖像服務和目錄](../extensibility/image-service-and-catalog.md),對高 DPI 和問題進行出色的圖像管理和支援。

## <a name="find-and-install-existing-visual-studio-extensions"></a>尋找並安裝現有的視覺化工作室擴展
 您可以在 **「工具**」功能表上的「**擴充和更新**」對話框中找到視覺化工作室擴展。 有關詳細資訊,請參閱[尋找和使用可視化工作室擴展](../ide/finding-and-using-visual-studio-extensions.md)。 您還可以在[可視化工作室市場](https://marketplace.visualstudio.com/)中找到擴展

## <a name="visual-studio-sdk-reference"></a>視覺化工作室 SDK 參考
 您可以在[可視化工作室 SDK 參考](../extensibility/visual-studio-sdk-reference.md)中找到可視化工作室 SDK API 參考。

## <a name="visual-studio-sdk-samples"></a>視覺化工作室 SDK 範例
 您可以在[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)的 GitHub 上找到 VS SDK 擴展的開源範例。 此 GitHub 儲存庫包含範例,這些範例說明了 Visual Studio 中的各種可擴充功能。

## <a name="other-visual-studio-sdk-resources"></a>其他視覺化工作室 SDK 資源
 如果您對 VSSDK 有疑問,或者想要分享開發擴展的經驗,您可以使用[可視化工作室擴展性論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS Gitter 聊天室](https://gitter.im/Microsoft/extendvs)。

 您可以在[VSX Arcana 部落格](https://blogs.msdn.microsoft.com/vsx/)與 Microsoft MVP 撰寫的許多部落格中找到更多資訊:

- [最喜歡的視覺工作室擴展](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [視覺工作室可擴充性](http://www.visualstudioextensibility.com/overview/vs/)

- [擴展視覺工作室](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>另請參閱

- [使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)
- [如何:將擴充性項目移到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [常見問題解答:將載入項轉換為 VSPackage 擴充](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [管理程式碼管理多個線程](../extensibility/managing-multiple-threads-in-managed-code.md)
- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
- [新增指令到工具列](../extensibility/adding-commands-to-toolbars.md)
- [擴充並自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)
- [編輯器和語言服務擴充](../extensibility/editor-and-language-service-extensions.md)
- [延伸項目](../extensibility/extending-projects.md)
- [擴充使用者設定與選項](../extensibility/extending-user-settings-and-options.md)
- [建立自訂項目與專案樣本](../extensibility/creating-custom-project-and-item-templates.md)
- [延伸屬性與屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
- [擴展視覺工作室的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)
- [使用與提供服務](../extensibility/using-and-providing-services.md)
- [管理 VSPackages](../extensibility/managing-vspackages.md)
- [視覺化工作室隔離外殼](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [船舶視覺工作室擴展](../extensibility/shipping-visual-studio-extensions.md)
- [深入探索 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [支援 Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [視覺化工作室 SDK 參考](../extensibility/visual-studio-sdk-reference.md)
