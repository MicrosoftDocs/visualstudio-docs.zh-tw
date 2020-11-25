---
title: 改善啟動時間
description: 瞭解如何在 [管理 Visual Studio 效能] 對話方塊中控制擴充功能和工具視窗的設定，以改善 Visual Studio 的啟動時間。
ms.custom: SEO-VS-2020
ms.date: 11/15/2017
ms.topic: how-to
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: a9cc3309e75e23ff325dd08ef9d2cceacb5f5db5
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871492"
---
# <a name="optimize-visual-studio-startup-time"></a>最佳化 Visual Studio 啟動時間

Visual Studio 設計旨在盡可能快速且有效率地啟動。 不過，某些 Visual Studio 延伸模組和工具視窗可能會在載入時對啟動時間有不利的影響。 您可以在 [管理 Visual Studio 效能] 對話方塊中控制緩慢延伸模組和工具視窗的行為。 如需提升效能的一般祕訣，請參閱 [Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)。

## <a name="startup-behavior"></a>啟動行為

為了避免延長啟動時間，Visual Studio 使用「隨需」的方式來載入延伸模組。 此行為代表延伸模組不會在 Visual Studio 立即開啟，而是視需要開啟。 此外，因為在先前的 Visual Studio 工作階段中保持開啟的工具視窗可能會讓啟動時間變慢，所以 Visual Studio 會以更智慧的方式開啟工具視窗，以避免影響啟動時間。

如果 Visual Studio 偵測到啟動變慢，就會出現快顯訊息，警告您導致速度變慢的延伸模組或工具視窗。 此訊息提供 [管理 Visual Studio 效能] 對話方塊的連結。 您也可以從功能表列選擇 [說明 **Help**  >  **管理 Visual Studio 效能**] 來存取此對話方塊。

![管理 Visual Studio 效能 - 快顯會顯示「我們注意到擴充功能 ... 讓 Visual Studio 變慢」的訊息](../ide/media/vside_perfdialog_popup.png)

對話方塊會列出影響啟動效能的擴充功能與工具視窗。 您可以變更延伸模組和工具視窗設定，以改善啟動效能。

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />變更延伸模組設定以改善啟動、解決方案載入，以及鍵入效能

1. 從功能表列選擇 [說明] > [管理 Visual Studio 效能]，開啟 [管理 Visual Studio 效能] 對話方塊。

    如果某個延伸模組讓 Visual Studio 啟動、解決方案載入或鍵入變慢，該延伸模組會出現在 [管理 Visual Studio 效能] 對話方塊的 [延伸模組] > [啟動] 下 (或 [解決方案載入] 或 [鍵入])。

    ![管理 Visual Studio 效能 - 擴充功能檢視](../ide/media/vside_perfdialog_extensions.png)

2. 選擇您想要停用的延伸模組，然後選擇 [停用] 按鈕。

您一律可以使用 [ **擴充管理員** ] 或 [ **管理 Visual Studio 效能** ] 對話方塊，在未來的會話中重新啟用延伸模組。

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />變更工具視窗設定以改善啟動時間

1. 從功能表列選擇 [說明] > [管理 Visual Studio 效能]，開啟 [管理 Visual Studio 效能] 對話方塊。

    如果工具視窗讓 Visual Studio 啟動時速度變慢，工具視窗會顯示在 [管理 Visual Studio 效能] 對話方塊的 [工具視窗] > [啟動] 下。

2. 選擇您想要變更行為的工具視窗。

3. 選擇下列三個選項之一：

   - **使用預設行為：** 工具視窗的預設行為。 保持選取這個選項不會改善啟動效能。

   - **啟動時不要顯示視窗**：開啟 Visual Studio 時，一律會關閉指定的工具視窗，即使您在前一個工作階段中開啟也是一樣。 您可以在需要時從適當的功能表開啟工具視窗。

   - **啟動時自動隱藏視窗**：如果已在前一個工作階段中開啟工具視窗，則此選項會在啟動時摺疊工具視窗的群組，以避免初始化工具視窗。 如果您經常使用工具視窗，這個選項是不錯的選擇。 工具視窗仍然可用，但不再對 Visual Studio 啟動時間造成負面影響。

     ![管理 Visual Studio 效能 - 工具視窗檢視](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Visual Studio 2017 的部分早期版本有一項稱為 **輕量型解決方案載入** 的功能。 在目前版本中，即便不使用輕量型解決方案載入，含有受控碼的大型解決方案載入速度也比過去更快。

## <a name="see-also"></a>另請參閱

- [最佳化 Visual Studio 效能](../ide/optimize-visual-studio-performance.md)
- [Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 部落格 - 使用 Visual Studio 2017 15.6 版更快速地載入解決方案](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
