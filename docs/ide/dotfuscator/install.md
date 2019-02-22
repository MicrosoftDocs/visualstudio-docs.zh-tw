---
title: 安裝 Dotfuscator Community Edition (CE)
ms.date: 06/22/2017
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, obfuscation, .NET, 免費, Visual Studio 2017, 安裝
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: 了解如何安裝 Visual Studio 2017 中隨附的免費 Dotfuscator Community Edition。
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d62b531bac02cedc5b1de5a7c69443cc97571281
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942047"
---
# <a name="install-dotfuscator-community-edition-ce"></a>安裝 Dotfuscator Community Edition (CE)

Visual Studio 2017 推出新的低影響安裝體驗。
如此一來，預設不會安裝 Dotfuscator Community Edition (Dotfuscator CE)。
不過，即使已安裝 Visual Studio，Dotfuscator CE 亦很容易安裝。

> [!NOTE]
> 除了 Visual Studio 隨附的 Dotfuscator CE 版本，PreEmptive Solutions 也會在其網站上定期提供更新版本。
> 如果您想要直接下載**最新版本**而不是從 Visual Studio 安裝，請**[按一下這裡移至 Dotfuscator 下載頁面][download]**。

## <a name="within-visual-studio"></a>在 Visual Studio 中

您可以從 Visual Studio IDE 安裝 Dotfuscator CE：

1. 在 [快速啟動] \(Ctrl + Q) 搜尋列中鍵入 `dotfuscator`。 <br/> <br/> ![快速啟動](media/install_from_vs_12.png) <br/> <br/>
2. 在 [快速啟動] 結果顯示畫面的「安裝」標題下，選取 [PreEmptive Protection - Dotfuscator (個別元件)]。
   * 但若看到「功能表」標題下的 [工具] - [PreEmptive Protection - Dotfuscator]，則已安裝 Dotfuscator CE。 如需使用方式詳細資料，請參閱[完整 Dotfuscator CE 使用者指南的入門頁面][get-started]。
3. [Visual Studio 安裝程式] 視窗即會啟動，預先設定安裝 Dotfuscator CE。
   * 您可能需要提供系統管理員認證才能繼續。
4. 關閉所有 Visual Studio IDE 執行個體。 <br/> <br/> ![按一下 [安裝]](media/install_from_vs_345.png) <br/> <br/>
5. 在 [Visual Studio 安裝程式] 視窗中，按一下 [安裝]。

安裝完成之後，您就可以開始使用 Dotfuscator CE。 如需詳細資料，請參閱[完整 Dotfuscator CE 使用者指南的入門頁面][get-started]。

## <a name="during-visual-studio-installation"></a>Visual Studio 安裝期間

如果您尚未安裝 Visual Studio 2017，您可以從 [Visual Studio 網站][2017-install]取得安裝程式。
執行時，它會顯示所選 Visual Studio 版本的安裝選項。

![安裝選項](media/install_ui.png)

然後，您就可以安裝 Dotfuscator CE 當作 Visual Studio 2017 的個別元件︰

1. 選取 [個別元件] 索引標籤。
2. 勾選 [程式碼工具] 下的 [PreEmptive Protection - Dotfuscator] 項目。<br/> <br/> ![個別元件](media/install_individually_12.png) <br/> <br/>
3. [摘要] 面板會在 [個別元件] 區塊下顯示 [PreEmptive Protection - Dotfuscator]。 <br/> <br/> ![摘要窗格](media/install_individually_3.png) <br/> <br/>
4. 為環境設定合適的任何詳細安裝設定。
5. 準備好安裝 Visual Studio 時，請按一下 [安裝] 按鈕。

安裝完成之後，您就可以開始使用 Dotfuscator CE。 如需詳細資料，請參閱[完整 Dotfuscator CE 使用者指南的入門頁面][get-started]。

## <a name="see-also"></a>另請參閱

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html