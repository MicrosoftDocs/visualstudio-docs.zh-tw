---
title: 自訂 IDE
description: Visual Studio for Mac 可以使用各種方式加以自訂，讓使用者能夠在符合其效率與審美需求的環境中開發應用程式。 本主題探討 Visual Studio for Mac 可調整以符合您需求的各種方式。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: f547662278d2ae01660312aff2708970a0a9300a
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190248"
---
# <a name="customizing-the-ide"></a>自訂 IDE

Visual Studio for Mac 可以使用各種方式加以自訂，讓使用者能夠在效率與審美方面符合其需求的環境中開發應用程式。 本文章探討 Visual Studio for Mac 可調整以符合您需求的各種方式。

## <a name="dark-theme"></a>深色佈景主題

![暗色調佈景主題檢視](media/customizing-the-ide-image7a.png)

您可以瀏覽至 [Visual Studio] > [喜好設定] > [環境] > [視覺化樣式]，然後從 [使用者介面佈景主題] 下拉式清單中選取所需的佈景主題，以在 Visual Studio for Mac 中切換佈景主題，如下圖中所示：

![暗色調佈景主題選取](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>當地語系化

Visual Studio for Mac 以下列 14 種語言進行當地語系化，使它可供更多開發人員存取：

* 簡體中文 - 中國
* 繁體中文 - 台灣
* 捷克文
* 法文
* 德文
* 英文
* 義大利文
* 日文
* 韓文
* 波蘭文
* 葡萄牙文 - 巴西
* 俄文
* 西班牙文
* 土耳其文

若要變更 Visual Studio for Mac 所顯示的語言，請瀏覽至 [Visual Studio] > [喜好設定] > [環境] > [視覺化樣式]，然後從 [使用者介面語言] 下拉式清單中選取所需語言，如下圖所示：

![語言選擇](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>作者資訊

作者資訊面板可讓您新增自己的相關資訊，例如姓名、電子郵件地址、作品的版權擁有者、公司及商標：

![編輯作者資訊區段](media/customizing-the-ide-image9a.png)

這項資訊用來填入標準檔案標題 (例如授權)，您可能會將這些標題加入新檔案：

![標準標題選項](media/customizing-the-ide-image8a.png)

填入的 [名稱] 和 [電子郵件] 欄位將在透過 Visual Studio for Mac 中的版本控制進行的任何認可中使用。 如果未填入這些欄位，Visual Studio for Mac 會在您嘗試使用版本控制時提示您這樣做。

## <a name="key-bindings"></a>按鍵繫結關係

按鍵繫結可讓您調整您的開發環境，以便能夠在 Visual Studio for Mac 中更有效率地行動。 它提供許多熱門 IDE 的常見按鍵繫結，例如 Visual Studio (在 Windows 上)、ReSharper、Visual Studio Code 和 Xcode。

您可以瀏覽至 [Visual Studio] > [喜好設定] > [環境] > [按鍵繫結] 來設定按鍵繫結，如下圖所示：

![設定按鍵繫結](media/customizing-the-ide-image10a.png)

從這裡您可以搜尋按鍵繫結組合、檢視衝突的繫結、新增繫結和編輯現有的繫結。

## <a name="workspace-layout"></a>工作區版面配置

Visual Studio for Mac 的工作區包含一個主要的文件區域 (通常是編輯器、設計工具介面或選項檔)，周圍伴隨的「板」則包含用於存取和管理應用程式檔案、測試及偵錯的實用資訊。

 ![工作區版面配置](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>檢視和排列板

當您在 Visual Studio for Mac 中開啟任何新的方案或檔案時，應該注意到工作區中存在一些「板」，包括 [Solution Pad]、[文件大綱] 和 [錯誤]：

![Solution Pad](media/customizing-the-ide-image2a.png)

Visual Studio for Mac 提供包含其他資訊、工具和瀏覽輔助工具的板，這些全都可透過瀏覽至 [檢視] > [板] 功能表項目，並選取面板來加以新增以進行存取：

![選取新板](media/customizing-the-ide-image3a.png)

板也可以透過各種不同的命令自動開啟，例如 **在檔案中尋找** (Shift + Cmd + F) 命令可開啟搜尋結果的卸離板。

板可以使用對您而言最有效益的任何方式在工作流程中移動或排列。 例如，它們可停駐在文件編輯器的任一側、另一個板的相鄰位置、另一個板的上方或下方，或者成為一組索引標籤板，讓您能夠在其間快速切換。

對於經常使用的面板，您也可以將面板從 Visual Studio for Mac 視窗中完全卸離，並為該面板建立另一個視窗。

透過每個板右上角的切換圖示可以隱藏和關閉這些板：

![隱藏和關閉板](media/customizing-the-ide-image5a.png)

自動隱藏的板會停駐在工作區的側邊，讓您在需要時能夠輕鬆存取這些板。 將滑鼠停留在板上時會重新顯示板，而在滑鼠和鍵盤焦點離開板時則會予以隱藏。

### <a name="organizing-layouts"></a>組織版面配置

任何時候顯示的板都是取決於目前的內容。 例如，使用視覺化設計工具時，工具箱和屬性方格板最重要；偵錯時，最好有偵錯工具板來檢視堆疊和區域變數。

「版面配置」代表已開啟板的狀態。 版面配置可透過 [檢視] 功能表手動切換 (如下圖所示)，或者在您執行某個動作 (例如偵錯或開啟分鏡腳本) 時自動切換：

![選取新的版面配置](media/customizing-the-ide-image6b.png)

一定有一個使用中的版面配置，您在版面配置中所做的任何變更 (例如新增或重新定位板) 只會變更使用中的版面配置。 關閉 Visual Studio for Mac 之後，將不會儲存您所做的變更。

不過，可以使用 [檢視] > [儲存目前版面配置] 功能表項目來建立新的版面配置。 這會將目前的版面配置新增至功能表，因此您可以隨時選取它：

![儲存目前的版面配置](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>並排編輯支援

Visual Studio for Mac 可讓您並排開啟文字編輯器，或以卸離的浮動視窗顯示編輯器。

2 欄模式可透過 [檢視] 功能表項目啟用，方法是選取 [檢視] > [編輯器資料行] > [2 欄]，或是將編輯器索引標籤拖曳到編輯器區域的其中一個邊緣：

![二欄的並行模式](media/customizing-the-ide-sbs.png)

編輯器索引標籤可以拖曳出文件區域來建立浮動的編輯器視窗。 此浮動視窗也支援並排的編輯器，而且可以包含數個編輯器索引標籤：

![建立新的視窗](media/customizing-the-ide-sbs1.png)

![二欄並排及其他索引標籤](media/customizing-the-ide-sbs2.png)

若要還原為單一開啟的編輯器，請選取 [檢視] > [Editor Columns] (編輯器資料欄) > [1 column] (單欄)。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>另請參閱

- [將 Visual Studio IDE 個人化 (在 Windows 上)](/visualstudio/ide/personalizing-the-visual-studio-ide)