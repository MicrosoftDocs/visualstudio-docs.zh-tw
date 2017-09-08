---
title: "最佳化 Visual Studio 啟動時間 | Microsoft Docs"
ms.custom: 
ms.date: 8/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>最佳化 Visual Studio 啟動時間
在理想情況下，Visual Studio 應該一律盡快啟動。 不過，Visual Studio 延伸模組和開啟工具視窗是在啟動時自動載入，因此可能會嚴重影響啟動時間。 [管理 Visual Studio 效能] 視窗可讓您查看影響 Visual Studio 啟動時間的擴充與功能，並控制這些擴充與功能的載入行為。

如需提升效能的一般提示，請參閱 [Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)。

## <a name="control-startup-behavior"></a>控制啟動行為

為了避免延長啟動時間，Visual Studio 2017 會使用依需求載入方式，以避免在啟動時載入擴充功能。 此行為代表擴充功能不會在 Visual Studio 啟動之後立即開啟，而是在啟動之後視需要來開啟。 此外，因為在先前的 Visual Studio 工作階段中保持開啟的工具視窗可能會讓啟動時間變慢，所以 Visual Studio 會以更智慧的方式開啟工具視窗，以避免影響啟動時間。

如果 Visual Studio 偵測到啟動變慢，就會出現快顯訊息，警告您導致速度變慢的延伸模組或工具視窗。 此訊息也會提供 [管理 Visual Studio 效能] 對話方塊的連結。 您也可以使用 [說明] > [管理 Visual Studio 效能] 功能表命令來開啟此視窗。

![管理 Visual Studio 效能 - 快顯會顯示「我們注意到擴充功能 ... 讓 Visual Studio 變慢」的訊息](../ide/media/vside_perfdialog_popup.png)

對話方塊會列出影響啟動效能的擴充功能與工具視窗。 這個對話方塊可讓您變更延伸模組和工具視窗設定，以改善啟動效能。

### <a name="change-extension-settings"></a>變更擴充功能設定

如果某個擴充功能讓 Visual Studio 啟動變慢，則在您選擇其中一種擴充功能類型時，該擴充功能會出現在 [管理 Visual Studio 效能] 對話方塊中。 對話方塊會顯示啟動時、載入方案時與在編輯器中輸入時，影響效能的擴充功能。

![管理 Visual Studio 效能 - 擴充功能檢視](../ide/media/vside_perfdialog_extensions.png)

對於啟動、方案載入或輸入時間的影響，如果高到無法接受的程度，請選取 [停用] 按鈕，以便為該案例停用擴充功能。 您隨時可以使用擴充管理員或 [管理 Visual Studio 效能] 對話方塊，針對未來的工作階段重新啟用擴充功能。

### <a name="change-tool-window-settings"></a>變更工具視窗設定

如果工具視窗讓 Visual Studio 啟動變慢，而您想要改變此一影響，則可以覆寫工具視窗的行為，方法是選取下列兩個選項其中之一來取代 [使用預設行為]：

- **啟動時不要顯示視窗**：下次開啟 Visual Studio 時，一律會關閉指定的工具視窗，即使已在前一個工作階段中開啟也是一樣。 您可以從適當的功能表中開啟工具視窗。
- **啟動時自動隱藏視窗**：如果已在前一個工作階段中開啟工具視窗，則此選項會在啟動時摺疊工具視窗的群組，以避免初始化工具視窗。 如果您經常使用工具視窗，則此選項是不錯的選擇，原因是工具視窗仍然可用，但不再對 Visual Studio 啟動時間造成負面影響。

![管理 Visual Studio 效能 - 工具視窗檢視](../ide/media/vside_perfdialog_toolwindows.png)

您隨時可以返回此對話方塊，以變更任何工具視窗的設定。

## <a name="speed_up_solution_load"></a>在 Visual Studio 2017 中更快地載入大型方案

Visual Studio 2017 導入一項稱為「輕量型解決方案載入」的新功能，可減少在 IDE 中載入大型方案所需的時間量和記憶體數量。 如果您有包含許多 C#、VB 或 C++ 專案的大型方案，則可能會在啟用輕量型解決方案載入時看到大幅效能改善。 如需此功能所提供優勢的詳細資訊，請參閱[最佳化方案載入](../ide/optimize-solution-loading-in-visual-studio)。

> [!NOTE]
> 此內容適用於 Visual Studio 2017 Update 3。

### <a name="enable-or-disable-lightweight-solution-load"></a>啟用或停用輕量型解決方案載入

以滑鼠右鍵按一下方案總管中的方案名稱，並選取 [啟用輕量型解決方案載入]。 選取選項之後，必須關閉並重新開啟方案，才能啟動輕量型解決方案載入。

![底下提供說明，包括方案總管](../ide/media/VSIDE_LSL_Solution_Setting.png)

若要設定輕量型解決方案載入的全域設定，請參閱[最佳化方案載入](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings)。

## <a name="see-also"></a>另請參閱
[Visual Studio 效能祕訣和訣竅](../ide/visual-studio-performance-tips-and-tricks.md)

