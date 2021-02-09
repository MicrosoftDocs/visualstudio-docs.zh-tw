---
title: 安裝 Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, obfuscation, .NET, 免費, Visual Studio 2017, Visual Studio 2019, Visual Studio, 安裝
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: 了解如何安裝 Visual Studio 中隨附的免費 Dotfuscator Community。
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 9f4ca634aa226437b6d8790837c9f95f778a00c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924764"
---
# <a name="install-dotfuscator-community"></a>安裝 Dotfuscator Community

Dotfuscator Community 是 Visual Studio 的選用元件。
這些指示說明其安裝方式。

> [!NOTE]
> 除了 Visual Studio 隨附的 Dotfuscator Community 版本，PreEmptive Solutions 也會在其網站上定期提供更新版本。
> 如果您想要直接下載 **最新版本** 而不是從 Visual Studio 安裝，請 **[按一下這裡移至 Dotfuscator 下載頁面][download]**。

## <a name="within-visual-studio"></a>在 Visual Studio 中

::: moniker range="vs-2019"

您可以從 Visual Studio IDE 安裝 Dotfuscator Community：

1. 在 **搜尋方塊** (Ctrl+Q) 中，輸入 `dotfuscator`。 <br/> <br/> ![搜尋方塊](media/install_in_vs19_12.png) <br/> <br/>

2. 在顯示的搜尋結果中，於 [元件] 標題下，選取 [安裝 PreEmptive Protection - Dotfuscator]。
   * 但您若在「功能表」標題下看到 [PreEmptive Protection - Dotfuscator Community]，則表示已安裝 Dotfuscator Community。 選取該選項，就可以[開始使用][get-started]。

3. 預先設定為安裝 Dotfuscator Community 的 [Visual Studio 安裝程式] 視窗，隨即會啟動。
   > [!NOTE]
   > 您可能需要提供系統管理員認證才能繼續。

4. 在 [Visual Studio 安裝程式] 視窗中，按一下 [安裝]。 <br/> <br/> ![按一下 [安裝]](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

您可以從 Visual Studio IDE 安裝 Dotfuscator Community：

1. 在 [快速啟動] \(Ctrl + Q) 搜尋列中鍵入 `dotfuscator`。 <br/> <br/> ![快速啟動](media/install_from_vs_12.png) <br/> <br/>

2. 在 [快速啟動] 結果顯示畫面的「安裝」標題下，選取 [PreEmptive Protection - Dotfuscator (個別元件)]。
   * 如果您看到，請在 [**工具-先占式保護-Dotfuscator**] 下的 *功能表* 標題底下，Dotfuscator CE 已安裝。 選取該選項，就可以[開始使用][get-started]。

3. 預先設定為安裝 Dotfuscator CE 的 [Visual Studio 安裝程式] 視窗，隨即會啟動。
   > [!NOTE]
   > 您可能需要提供系統管理員認證才能繼續。

4. 在 [Visual Studio 安裝程式] 視窗中，按一下 [安裝]。 <br/> <br/> ![按一下 [安裝]](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

安裝完成之後，您就可以 [開始使用 Dotfuscator 社區][get-started]。

## <a name="during-visual-studio-installation"></a>Visual Studio 安裝期間

如果您尚未安裝 Visual Studio，您可以從 [Visual Studio 網站][vs-install]取得安裝程式。
執行時，它會顯示所選 Visual Studio 版本的安裝選項。

::: moniker range="vs-2019"

![安裝選項](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![安裝選項](media/install_ui_17.png)

::: moniker-end

然後，您就可以安裝 Dotfuscator Community 當作 Visual Studio 的個別元件︰

1. 選取 [個別元件] 索引標籤。
2. 勾選 [程式碼工具] 下的 [PreEmptive Protection - Dotfuscator] 項目。<br/> <br/> ![個別元件](media/install_individually_12.png) <br/> <br/>
3. [摘要] 面板會在 [個別元件] 區塊下顯示 [PreEmptive Protection - Dotfuscator]。 <br/> <br/> ![摘要窗格](media/install_individually_3.png) <br/> <br/>
4. 為環境設定合適的任何詳細安裝設定。
5. 準備好安裝 Visual Studio 時，請按一下 [安裝] 按鈕。

安裝完成之後，您就可以開始使用 Dotfuscator Community。 如需詳細資料，請參閱[完整 Dotfuscator Community 使用者指南的使用者入門頁面][get-started]。

## <a name="see-also"></a>另請參閱

[完整《Dotfuscator Community 使用者指南》中的本主題](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
