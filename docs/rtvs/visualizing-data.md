---
title: "使用 Visual Studio R 工具的視覺化資料 | Microsoft Docs"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496619c9-4005-4c20-baf6-80b4bb1ceb56
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 48aaf1c8e02c1de84c36d8bff7d9b73eb4bd3af7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-visual-data-plots-with-r"></a>以 R 建立視覺化資料繪圖

繪圖是資料科學家工作流程的重要部分。 在 Visual Studio R 工具 (RTVS) 中，所有繪圖活動都著重於一或多個繪圖視窗，其設計旨在以此重要活動來提升生產力。

![繪製英雄影像](media/plotting-hero-image.png)

本主題內容：

- [繪圖視窗](#the-plot-window)
- [多個繪圖視窗](#multiple-plot-windows)
- [繪圖歷程記錄](#plot-history)
- [以程式設計方式操作繪圖視窗](#programmatically-manipulating-plot-windows)

下列影片 (2 分 02 秒) 簡短介紹 RTVS 中的繪圖︰

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZTbKmz5RSgY" frameborder="0" allowfullscreen></iframe>

## <a name="the-plot-window"></a>繪圖視窗

繪圖視窗保留一系列的繪圖，每份繪圖皆由 `plot` 命令產生。 例如，如果其中一個已無法使用，則使用 `plot(1:100)` 建立新的繪圖視窗︰

![1 到 100 之間的線性繪圖](media/plotting-1-to-100.png)

就技術上而言，R `plot` 命令會將其輸出呈現在 R 圖形裝置，繪圖視窗則呈現 R 圖形裝置的內容，這就是每個繪圖視窗都有裝置編號的原因。

繪圖視窗不受 Visual Studio 專案影響，當您載入及關閉專案時都保持開啟。

產生繪圖會使用「使用中」繪圖視窗，並儲存任何先前繪圖的歷程記錄 (請參閱[繪圖歷程記錄](#plot-history))。 例如，輸入 `plot(100:1)`，而第一個繪圖會取代為向下線條。

如同所有其他 Visual Studio 視窗一樣。 繪圖視窗支援自訂的版面配置 (請參閱[在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md))。 繪圖視窗可以停駐在 Visual Studio 框架內的不同位置、在該框架內調整大小，或從框架中整個提取出來獨立調整大小。 

調整繪圖視窗的大小一律會重新繪圖，以提供最佳品質的影像。 您通常會想要先調整繪圖大小，再使用下一節描述的命令將繪圖匯出至檔案或剪貼簿。

## <a name="plot-window-commands"></a>繪圖視窗命令

繪圖視窗工具列保留適用的命令，其中大部分也都可透過 [R 工具] > [繪圖] 功能表取得。

| 按鈕 | 命令 | 說明 | 
| --- | --- | --- |
| ![新增繪圖視窗按鈕](media/plotting-toolbar-01-new-plot-window.png) | 新增繪圖視窗 | 建立有專屬歷程記錄的個別繪圖視窗。 請參閱[多個繪圖視窗](#multiple-plot-windows)。 |
| ![啟動繪圖視窗按鈕](media/plotting-toolbar-02-activate-plot-window.png) | 啟動繪圖視窗 | 將目前的繪圖視窗設為使用中視窗，以便後續的 `plot` 命令呈現在該視窗中。 請參閱[多個繪圖視窗](#multiple-plot-windows)。 請參閱[多個繪圖視窗](#multiple-plot-windows)。 |
| ![繪圖歷程記錄視窗按鈕](media/plotting-toolbar-03-plot-history.png) | 繪圖歷程記錄視窗 | 開啟視窗，內含歷程記錄中顯示為縮圖的所有繪圖。 請參閱[繪圖歷程記錄](#plot-history)。 |
| ![繪圖歷程記錄按鈕](media/plotting-toolbar-04-plot-history-arrows.png) | 上一張/下一張繪圖 |  巡覽歷程記錄中的上一張或下一張繪圖。 您也可以使用 Ctrl+Alt+F11 ([上一張]) 和 Ctrl+Alt+F12 ([下一張]) 巡覽歷程記錄。 請參閱[繪圖歷程記錄](#plot-history)。 |
| ![另存成影像按鈕](media/plotting-toolbar-05-save-as-image.png)| 另存成影像 | 提示輸入檔案名稱，並將目前的繪圖 (視窗大小的視窗內容) 儲存為影像檔案。 可用的格式為 `.png`、`.jpg`、`.bmp` 和 `.tif`。 |
| ![儲存為 PDF 按鈕](media/plotting-toolbar-06-save-as-pdf.png)| 儲存為 PDF | 將目前的繪圖儲存為 PDF 檔案，使用目前的視窗大小。 如果調整 PDF，會重新呈現繪圖。 |
| ![複製為點陣圖按鈕](media/plotting-toolbar-07-copy-as-bitmap.png)| 複製為點陣圖 | 將繪圖複製到剪貼簿中成為點陣圖，使用目前的視窗大小。 | 
| ![複製為中繼檔按鈕](media/plotting-toolbar-08-copy-as-metafile.png)| 複製為中繼檔 | 將繪圖複製到剪貼簿成為 [Windows 中繼檔](https://en.wikipedia.org/wiki/Windows_Metafile) (維基百科)。 | 
| ![移除繪圖按鈕](media/plotting-toolbar-09-remove-plot.png)| 移除繪圖 | 從歷程記錄中移除目前的繪圖。 |
| ![清除所有繪圖按鈕](media/plotting-toolbar-10-clear-all-plots.png) | 清除所有繪圖 | 從歷程記錄中清除所有繪圖 (提示使用者進行確認)。 |

## <a name="multiple-plot-windows"></a>多個繪圖視窗

因為資料科學家通常會使用來自許多不同資料集的許多繪圖，所以 RTVS 可讓您建立所要數目的獨立繪圖視窗。 不過，您可以接著在 Visual Studio 框架內部或該框架外部，依您想要的方式排列這些視窗。 (如需停駐和調整視窗大小的一般資訊，請參閱[在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。)

使用工具列按鈕或 [R 工具] > [繪圖] > [新增繪圖視窗]，建立新的繪圖視窗。 新的繪圖視窗變成「使用中」視窗，也就是呈現新繪圖的位置。 若要變更使用中視窗，請切換到該視窗，然後選取 [啟動繪圖視窗] 工具列按鈕或 [R 工具] > [繪圖] > [啟動繪圖視窗]。

繪圖也是獨立物件，這表示您可以在繪圖視窗間複製或移動它們，方法是使用滑鼠拖放，或使用滑鼠右鍵操作功能表和 [編輯] 功能表的 [複製]、[剪下] 和 [貼上] 命令。

預設的拖放行為是複製；若要移動，拖曳時請按住 Shift 鍵。

## <a name="plot-history"></a>繪圖歷程記錄

繪圖命令會保留在每個視窗的繪圖歷程記錄中，確保留存工作階段中的所有繪圖作業。 若要巡覽歷程記錄，請使用繪圖視窗工具列上的箭號按鈕，或使用 Ctrl+Alt+F11 和 Ctrl+Alt+F12。 您也可以再次使用工具列按鈕或 [R 工具] > [繪圖] 功能表命令，從視窗中移除單一繪圖或清除所有繪圖。

若要查看整個繪圖集合，請使用工具列按鈕或 [R 工具] > [繪圖] > [繪圖歷程記錄視窗]，開啟 [繪圖歷程記錄視窗]。
歷程記錄會提供您一份在該視窗中顯示的繪圖縮圖清單，並依不同的繪圖視窗 (或裝置) 分組。 使用工具列上的縮放按鈕可變更縮圖的大小。

![繪圖歷程記錄視窗](media/plotting-plot-history-window.png)

若要在相關聯的視窗中開啟繪圖，請按兩下該繪圖、選取它，然後選取 [顯示繪圖] 工具列按鈕，或以滑鼠右鍵按一下並選取 [顯示繪圖]。 您也可以選取個別的繪圖，從滑鼠右鍵操作功能表或 [編輯] 功能表中複製、剪下或刪除。

所有視窗的繪圖歷程記錄存留期都會繫結至互動式 R 工作階段的存留期。 如果您重設 R 工作階段，或結束並重新啟動 Visual Studio，就會重設您的繪圖歷程記錄。

## <a name="programmatically-manipulating-plot-windows"></a>以程式設計方式操作繪圖視窗

您可利用裝置編號識別特定的繪圖視窗，使用 R 程式碼以程式設計方式操作繪圖視窗。 

- `dev.list()`︰列出目前 R 工作階段內所有的圖形裝置。
- `dev.new()`︰建立新的圖形裝置 (新的繪圖視窗)。
- `dev.set(<device number>)`︰設定使用中的圖形裝置。
- `dev.off()`︰刪除使用中的裝置。
