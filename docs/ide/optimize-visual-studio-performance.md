---
title: Visual Studio 變慢時改善效能
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: c56bd7bbfdd162a354432814decb2450eff6f360
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070457"
---
# <a name="optimize-visual-studio-performance"></a>最佳化 Visual Studio 效能

本文提供在發現 Visual Studio 執行速度變慢時要嘗試的一些建議。 如需如何改善效能的建議，您也可以查看 [Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)。

## <a name="upgrade-to-visual-studio-2017-version-156-or-later"></a>升級至 Visual Studio 2017 15.6 版或更新版本

如果您目前使用 Visual Studio 2015，請免費下載 [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 簽出其改善的效能。 Visual Studio 2017 中的解決方案載入速度快兩或三倍，而其他領域的效能也會改善。 Visual Studio 2017 與 Visual Studio 2015 並存相容，因此您試用並不會遺失任何項目。

如果您目前使用 Visual Studio 2017，則請確定執行 15.6 版或更新版本。 資料顯示 15.6 版中的解決方案載入速度快兩或三倍。 在[這裡](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)下載。

## <a name="extensions-and-tool-windows"></a>延伸模組和工具視窗

您可能已安裝讓 Visual Studio 變慢的延伸模組。 如需管理延伸模組以改善效能的說明，請參閱[變更延伸模組設定以改善效能](../ide/optimize-visual-studio-startup-time.md#extensions)。

同樣地，您可能會有減緩 Visual Studio 的工具視窗。 如需管理工具視窗的說明，請參閱[變更工具視窗設定以改善效能](../ide/optimize-visual-studio-startup-time.md#tool-windows)。

## <a name="hardware"></a>硬體

如果您想要升級硬體，固態硬碟 (SSD) 的效能會優於額外 RAM 或更快的 CPU。

如果您新增 SSD，則為了獲得最佳效能，請在該磁碟機上安裝 Windows，而不是硬碟機 (HDD)。 Visual Studio 解決方案的磁碟機位置似乎不重要。

此外，請不要從 USB 磁碟機執行您的解決方案。 請將它複製至您的 HDD 或 SSD。

## <a name="help-us-improve"></a>協助我們改善

您的意見反應可協助我們改善。 使用 [回報問題] 功能，「記錄」追蹤，並將它傳送給我們。 選取 [快速啟動] 旁的意見反應圖示，或從功能表列中選取 [說明] > [傳送意見反應] > [回報問題]。 如需詳細資訊，請參閱[如何回報 Visual Studio 2017 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)。

## <a name="see-also"></a>另請參閱

- [效能秘訣與訣竅](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 部落格 - 使用 Visual Studio 2017 15.6 版更快速地載入解決方案](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)