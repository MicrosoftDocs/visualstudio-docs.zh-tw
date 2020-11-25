---
title: Visual Studio 變慢時改善效能
titleSuffix: ''
description: 瞭解如何改善 Visual Studio 效能，如果您發現它的執行速度很慢。
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6e6f93b7709144e6682bc54d5686fde5ff650f56
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871466"
---
# <a name="optimize-visual-studio-performance"></a>最佳化 Visual Studio 效能

本文提供在發現 Visual Studio 執行速度變慢時要嘗試的一些建議。 如需如何改善效能的建議，您也可以查看 [Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)。

## <a name="upgrade-visual-studio"></a>升級 Visual Studio

如果您目前使用 Visual Studio 2015，請免費下載 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 或 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 以查看其改善的效能。 其方案載入速度比 Visual Studio 2015 快二到三倍，而其他領域的效能亦有改善。 Visual Studio 2015 與 Visual Studio 2017 和 Visual Studio 2019 並存相容，試用看看並不會造成任何損失。

::: moniker range="vs-2017"

如果您已在使用 Visual Studio 2017，請確認執行的是 15.6 版或更新版本。 資料顯示 15.6 版中的解決方案載入速度快兩或三倍。 在 [這裡](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)下載。

::: moniker-end

## <a name="extensions-and-tool-windows"></a>延伸模組和工具視窗

您可能已安裝讓 Visual Studio 變慢的延伸模組。 如需管理延伸模組以改善效能的說明，請參閱[變更延伸模組設定以改善效能](../ide/optimize-visual-studio-startup-time.md#extensions)。

同樣地，您可能會有減緩 Visual Studio 的工具視窗。 如需管理工具視窗的說明，請參閱[變更工具視窗設定以改善效能](../ide/optimize-visual-studio-startup-time.md#tool-windows)。

## <a name="hardware"></a>硬體

如果您想要升級硬體，固態硬碟 (SSD) 的效能會優於額外 RAM 或更快的 CPU。

如果您新增 SSD，則為了獲得最佳效能，請在該磁碟機上安裝 Windows，而不是硬碟機 (HDD)。 Visual Studio 解決方案的磁碟機位置似乎不重要。

此外，請不要從 USB 磁碟機執行您的解決方案。 請將它複製至您的 HDD 或 SSD。

## <a name="help-us-improve"></a>協助我們改善

您的意見反應可協助我們改善。 使用 [回報問題] 功能，「記錄」追蹤，並將它傳送給我們。 選取 [快速啟動] 旁的意見反應圖示，或從功能表列中選取 [說明] > [傳送意見反應] > [回報問題]。 如需詳細資訊，請參閱[如何回報 Visual Studio 的問題](../ide/how-to-report-a-problem-with-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [效能秘訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 部落格 - 使用 Visual Studio 2017 15.6 版更快速地載入解決方案](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
