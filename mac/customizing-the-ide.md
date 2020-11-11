---
title: 自訂 IDE
description: Visual Studio for Mac 可以使用各種方式加以自訂，讓使用者能夠在符合其效率與審美需求的環境中開發應用程式。 本文將探討 Visual Studio for Mac 可調整以符合您需求的各種方式。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: 05fd1091a279a085c2a727eb36cbc56fcb201057
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493285"
---
# <a name="customizing-the-ide"></a>自訂 IDE

Visual Studio for Mac 可以自訂，讓使用者能夠在符合其需求的環境中開發應用程式，以達到效率和美學。 本文章探討 Visual Studio for Mac 可調整以符合您需求的各種方式。

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

填入的 [名稱] 和 [電子郵件] 欄位將在透過 Visual Studio for Mac 中的版本控制進行的任何認可中使用。 如果您尚未填入這些欄位，Visual Studio for Mac 會在您嘗試使用版本控制時提示您這樣做。

## <a name="key-bindings"></a>按鍵繫結關係

按鍵系結或鍵盤快速鍵可讓您調整您的開發環境，讓您可以在 Visual Studio for Mac 之間更有效率地移動。 它提供許多熱門 IDE 的常見按鍵繫結，例如 Visual Studio (在 Windows 上)、ReSharper、Visual Studio Code 和 Xcode。

您可以瀏覽至 [Visual Studio] > [喜好設定] > [環境] > [按鍵繫結] 來設定按鍵繫結，如下圖所示：

![設定按鍵繫結](media/customizing-the-ide-image10a.png)

從這裡您可以搜尋按鍵繫結組合、檢視衝突的繫結、新增繫結和編輯現有的繫結。

您也可以在 Visual Studio for Mac 的初始安裝期間，透過 **鍵盤選取** 畫面來設定這些系結：

![設定金鑰系結，第一次執行](media/ide-tour-2019-keyboard-shortcut.png)

## <a name="workspace-layout"></a>工作區版面配置

Visual Studio for Mac 的工作區是由一個主要檔區域所組成 (通常是編輯器、設計工具介面或選項檔) ，並包含可存取和管理應用程式檔、測試和偵錯工具的實用資訊，包含有用的 *工具視窗* 。

 ![工作區版面配置](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-tool-windows"></a>查看和排列工具視窗

當您在 Visual Studio for Mac 中開啟任何新的方案或檔案時，應該會注意到工作區中的一些 *工具視窗* ，包括 [方案] 視窗、[檔大綱] 和 [錯誤]：

![工具視窗](media/customizing-the-ide-image2a.png)

Visual Studio for Mac 提供包含其他資訊、工具和導覽輔助工具的工具視窗，您可以流覽 [ **View** ] 功能表項目並選取要加入的工具視窗，以存取這些工具視窗：

![選取新的工具視窗](media/customizing-the-ide-image3a.png)

不同的命令也可以自動開啟工具視窗，例如 [在檔案 **中尋找** ] (Shift + Cmd + F) 命令，這會開啟已卸離的搜尋結果視窗。

您可以透過任何最適合您的方式，在整個工作流程中移動和排列工具視窗。 例如，它們可以停駐在檔編輯器的任何一邊、與其他工具視窗相鄰、位於另一個視窗的上方或下方，或作為一組索引標籤式視窗，讓您快速切換它們。

針對常用的工具視窗，您也可以將它們從 Visual Studio for Mac 視窗和各自的新視窗中完全卸離。

您可以透過每個視窗右上角的控制項來釘選和關閉工具視窗：

:::image type="content" source="media/customizing-the-ide-image5a.png" alt-text="使用控制項釘選或關閉工具視窗":::

固定的視窗會停駐在工作區的側邊，並在您需要時保持開啟，以加快存取的速度。 停用的視窗是固定的，但在您將滑鼠停留在視窗的索引標籤上，並將滑鼠或焦點放在鍵盤上時，才會顯示：當滑鼠和鍵盤焦點離開它們時，就可以隱藏它們。

### <a name="organizing-layouts"></a>組織版面配置

在任何時間顯示的工具視窗都取決於目前的內容。 例如，使用視覺化設計工具時，[工具箱] 和 [屬性方格] 視窗最重要;在進行偵錯工具時，讓偵錯工具視窗能夠用來查看堆疊和區域變數會很有用。

開啟的工具視窗狀態 *是以配置表示。* 您可以透過 [View] 功能表以手動方式切換配置（如下圖所示），或在您執行動作（例如，偵錯工具或開啟分鏡腳本）時自動切換版面配置：

![選取新的版面配置](media/customizing-the-ide-image6b.png)

您可以使用 View > Layout 來建立新的版面配置 **> 儲存目前的版面** 配置 ... 功能表項目。 此命令會將您目前的版面配置新增至功能表，讓您可以隨時選取它：

![儲存目前的版面配置](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>並排編輯支援

Visual Studio for Mac 可讓您並排開啟文字編輯器，或以卸離的浮動視窗顯示編輯器。

您可以透過 [View] 功能表項目，藉由選取 [ **view > Editor columns] > 2** 個數據行，或將編輯器索引標籤拖曳到編輯器區域的其中一個邊緣，以啟用兩個數據行模式：

![二欄的並行模式](media/customizing-the-ide-sbs.png)

編輯器索引標籤可以拖曳出文件區域來建立浮動的編輯器視窗。 此浮動視窗也支援並排的編輯器，而且可以包含數個編輯器索引標籤：

![建立新的視窗](media/customizing-the-ide-sbs1.png)

![二欄並排及其他索引標籤](media/customizing-the-ide-sbs2.png)

若要還原為單一開啟的編輯器，請選取 [檢視] > [Editor Columns] (編輯器資料欄) > [1 column] (單欄)。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>請參閱

- [將 Visual Studio IDE 個人化 (在 Windows 上)](/visualstudio/ide/personalizing-the-visual-studio-ide)