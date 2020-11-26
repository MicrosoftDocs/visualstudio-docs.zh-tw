---
title: 重構程式碼
description: 使用 Visual Studio for Mac 和快速動作來細分程式碼。
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3892117e5c84a71f258d4e019105fca0a8cf9c5b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189234"
---
# <a name="refactoring"></a>重構

重構程式碼是重新排列、重建和釐清現有程式碼的方法，並能同時確保程式碼的整體行為不會變更。

重構會產生較健康的程式碼基底，以讓您、任何其他開發人員或可能參考程式碼的使用者更容易使用、讀取和維護它。

Visual Studio for Mac 與 Roslyn (Microsoft 的開放原始碼 .NET 編譯器平台) 的整合，可讓您進行更多重構作業。

## <a name="renaming"></a>重新命名

[重新命名] 重構命令可以用於任何程式碼識別碼 (例如，類別名稱、屬性名稱等等)，以尋找該識別碼的所有出現項目並進行變更。 若要重新命名符號，請以滑鼠右鍵按一下它，然後選擇 [重新命名]，或使用 **Cmd (⌘) + R** 按鍵繫結關係：

![重新命名功能表項目](media/refactoring-renaming1.png)

這將醒目提示符號和其任何參考。 當您開始鍵入新名稱時，您程式碼中的所有參考都會自動變更，您可以按 **Enter** 認可變更：

![重新命名和識別碼](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>快速動作及重構

快速動作和重構可讓您輕鬆地重構、產生或以單一動作修改程式碼。

快速動作可用於：

* 針對程式碼分析器規則的違規情況套用程式碼修正
* 隱藏程式碼分析器規則的違規情況
* 套用重構作業 (例如，內嵌暫存變數)
* 產生程式碼 (例如，引進區域變數)

您可以使用燈泡燈泡 ![ 圖示 ](media/quick-actions-light-bulb-icon.png) 或螺絲螺絲螺絲起子圖示圖示來套用快速動作 ![ ](media/quick-actions-screwdriver-icon.png) ，或按下 **選項 (⌥)** + **Enter** 鍵（當游標位於可使用動作的程式程式碼上時）。 如果有紅色波浪線指出錯誤，而且 Visual Studio 有該錯誤可用的修正程式，您就會看到錯誤燈泡 ![錯誤燈泡圖示](media/quick-actions-error-light-bulb-icon.png)。

好比說，協力廠商可以針對任何語言，在 SDK 當中提供自訂診斷和建議，而 Visual Studio 燈泡會依據這些規則亮燈。

### <a name="quick-action-icons"></a>快速動作圖示
當有快速動作可用時，顯示的圖示會指出可用的修正或重構類型。 「螺絲起子」 ![螺絲起子圖示](media/quick-actions-screwdriver-icon.png)圖示表示有可變更程式碼的動作，但不一定要使用。 「黃色燈泡」 ![燈泡圖示](media/quick-actions-light-bulb-icon.png)圖示表示有「應」執行的動作，以改善程式碼。 「錯誤燈泡」 ![錯誤燈泡圖示](media/quick-actions-error-light-bulb-icon.png)圖示表示有動作可修正您程式碼中的錯誤。

### <a name="to-see-a-light-bulb-or-screwdriver"></a>顯示燈泡或螺絲起子

- 如果有可用的修正，燈泡會在您將滑鼠暫留於錯誤位置的同時顯示。

   ![當滑鼠游標暫留時的燈泡](media/refactoring-lightbulb-hover.png)

- 當您將插入號移至可使用快速動作或重構的程式程式碼時，會在編輯器的左邊界中顯示 Light 燈泡和螺絲起子。

- 按 **選項 (⌥)** + 在行上的任意處 **輸入**，以查看可用的快速動作和重構清單。

![顯示內容項目](media/refactoring-context-action.png)

將滑鼠游標移至任何內容動作上方，會提供從程式碼所新增或移除項目的預覽。

![選項輸入內容項目](media/refactoring-image2a.png)

若要啟用這些選項，您必須選取 [Visual Studio for Mac] > [喜好設定] > [文字編輯器] > [來源分析] 選項中的 [啟用開啟檔案的來源分析]：

![啟用來源分析](media/refactoring-options.png)

可建議超過 100 個可能的動作，其啟用或停用方式是瀏覽至 [Visual Studio for Mac] > [喜好設定] > [來源分析] > [C#] > [程式碼動作]，並選取或取消選取動作旁的方塊：

![C# 來源分析動作](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>一般快速動作

您可以在[一般快速動作](/visualstudio/ide/common-quick-actions)一文章深入了解一般快速動作。

## <a name="source-analysis"></a>來源分析

來源分析透過將潛在錯誤和樣式違規加上底線，並將自動修正提供為內容動作，來即時分析您的程式碼。

檢視文字編輯器右側的捲軸，即可隨時檢視任何檔案的所有來源分析結果：

![來源分析提要欄位](media/refactoring-image4a.png)

如果您按一下頂端的圓圈，則可以逐一查看每項建議，而最高嚴重性問題會顯示在最前面。 將滑鼠游標移至個別結果或個別行上方即會顯示問題，這可透過內容動作進行修正：

![來源分析項目](media/refactoring-image5.png)

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>另請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
