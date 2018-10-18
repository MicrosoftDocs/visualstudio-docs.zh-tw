---
title: 最佳化 Visual Studio 啟動時間 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4112edc991581444e2cfe81aeb25698f69899f82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283539"
---
# <a name="optimize-visual-studio-startup-time"></a>最佳化 Visual Studio 啟動時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在理想情況下，Visual Studio 應該一律盡快啟動。 不過，Visual Studio 延伸模組和開啟工具視窗是在啟動時自動載入，因此可能會嚴重影響啟動時間。 [管理 Visual Studio 效能] 視窗不只可讓您看到影響 Visual Studio 啟動時間的延伸模組和功能，還可讓您決定其載入行為，以進一步控制 Visual Studio 的啟動速度。

## <a name="control-startup-behavior"></a>控制啟動行為

為了避免延長啟動時間，Visual Studio"15"可避免載入延伸模組在啟動期間，使用依需求載入方式。 這表示延伸模組不會在 Visual Studio 啟動之後立即開啟，而是在啟動之後視需要非同步開啟。 此外，因為在先前的 Visual Studio 工作階段中保持開啟的工具視窗可能會讓啟動時間變慢，所以 Visual Studio 會以更智慧的方式開啟工具視窗，以避免影響啟動時間。

如果 Visual Studio 偵測到啟動變慢，就會出現快顯訊息，警告您導致速度變慢的延伸模組或工具視窗。 此訊息也會提供 [管理 Visual Studio 效能] 對話方塊的連結，而在此對話方塊中，會列出影響啟動效能的延伸模組和工具視窗。 這個對話方塊可讓您變更延伸模組和工具視窗設定，以改善啟動效能。

![管理 Visual Studio 效能 - 快顯視窗](../ide/media/vside-perfdialog-popup.PNG "管理 Visual Studio 效能 - 快顯視窗")

[管理 Visual Studio 效能] 對話方塊有兩種分類︰[延伸模組] 和 [工具視窗]。

### <a name="control-extensions"></a>控制延伸模組
如果延伸模組讓 Visual Studio 啟動變慢，則在您選擇其中一種延伸模組類型時，該延伸模組會出現在 [管理 Visual Studio 效能] 對話方塊中。 如果對啟動時間的影響 (列在 [影響] 區段下) 過高，您可以選擇 [停用] 按鈕來選擇一律在啟動時停用延伸模組。 您可以使用延伸模組管理員或 [管理 Visual Studio 效能] 對話方塊，針對未來的工作階段重新啟用延伸模組。

![管理 Visual Studio 效能 - 延伸模組](../ide/media/vside-perfdialog-extensions.PNG "管理 Visual Studio 效能 - 延伸模組")

除了啟動延伸模組之外，您也可以停用在載入方案時或使用者輸入時所載入的延伸模組。 只要選擇案例，就可以查看相關聯延伸模組的清單。

### <a name="control-tool-windows"></a>控制工具視窗
如果工具視窗會讓 Visual Studio 啟動變慢，您可以選擇保留其預設行為 (這對啟動速度沒有任何用處)，也可以選擇兩種行為中的其中一種行為來覆寫其行為：

- **啟動時不要顯示視窗**：如果您選擇此選項，則一律會在開啟 Visual Studio 時關閉指定的工具視窗，即使已在前一個工作階段中開啟也是一樣。 您可以從功能表開啟工具視窗。
- **啟動時自動隱藏視窗**：如果已在前一個工作階段中開啟工具視窗，則選擇此選項會在啟動時摺疊工具視窗的群組，以避免初始化工具視窗。 如果您經常使用工具視窗，則這是不錯的選擇，原因是工具視窗仍然可用，但不再對 Visual Studio 啟動時間造成負面影響。

![管理 Visual Studio 效能 - 工具視窗](../ide/media/vside-perfdialog-toolwindows.PNG "管理 Visual Studio 效能 - 工具視窗")

如果您稍後改變心意，則可以在 [管理 Visual Studio 效能] 對話方塊中還原所有這些選項。 若要開啟 [管理 Visual Studio 效能] 對話方塊，請在功能表列上依序選擇 [說明] 和 [管理 Visual Studio 效能]。


