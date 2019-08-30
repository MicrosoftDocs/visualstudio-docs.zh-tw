---
title: IntelliSense
description: 在 Visual Studio for Mac 中使用 IntelliSense 的資訊
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 3e99c31b1ab4d12532d701e4626ac9c1aae7df56
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026567"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense 提供數個功能，可協助增強撰寫和編輯程式碼的體驗。 例如，除了程式碼完成之外，IntelliSense 引擎也提供成員清單、參數資訊和快速諮詢。

在 Visual Studio for Mac 中，IntelliSense 是由核心編輯器服務提供，且支援多種語言，例如 C#、XAML、F#、JavaScript 等。 Visual Studio for Mac 也提供進階 IntelliSense 功能，例如能夠從程式庫顯示尚未匯入專案的完成項目。

## <a name="code-completion"></a>程式碼完成

在支援的檔案 (例如 C# 程式碼檔案) 中鍵入時，會在完成清單中顯示對您目前鍵入字串有效的完成項目，並隨著您鍵入的內容進行更新。 此外，如果您刪除文字，此清單會再次自動更新，以包含完成指定字串的更多可能性。 

完成視窗也支援依類型篩選包含的完成項目。 例如，您可以限制清單的成員只代表類型 (如類別或委派)。 您可以透過按一下代表所要篩選類型的特定圖示，或經由對應於指定類型的鍵盤快速鍵來啟用此篩選程序。 這些圖示位於完成視窗的底部，如下所示：

| 圖示                         | 名稱          | 關鍵字    | 熱鍵 |
| -----------------------------|---------------| -----------|--------|
| ![類別圖示](media/classes-icon.png)  | Class - 類別         | `class`    |  ⌥C
| ![常數圖示](media/constant-icon.png) | 常數      | `const`    |  ⌥O
| ![委派圖示](media/delegate-icon.png) | Delegate - 委派      | `delegate` |  ⌥D
| ![列舉圖示](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![事件圖示](media/event-icon.png)    | event         |            |  ⌥V
| ![欄位圖示](media/fields-icon.png)   | Field - 欄位         |            |  ⌥F
| ![介面圖示](media/interface-icon.png)| interface     | `interface`|  ⌥I
| ![關鍵字圖示](media/keyword-icon.png)  | keyword       |            |  ⌥K
| ![方法圖示](media/method-icon.png)   | 方法        |            |  ⌥M
| ![命名空間圖示](media/namespace-icon.png)| namespace     | `namespace`|  ⌥N
| ![屬性圖示](media/props-icon.png)    | 屬性      |            |  ⌥P
| ![程式碼片段圖示](media/snippet-icon.png)  | snippet       | `class`    |  ⌥S
| ![結構圖示](media/struct-icon.png)   | 結構     | `struct`   |  ⌥S

藉由按一下任何圖示，或是按下對應的快速鍵，完成清單就會僅限於篩選集所定義的類型。  

![Intellisense 類型篩選](media/intellisense-typefiltering.gif)

## <a name="show-import-items"></a>顯示匯入項目

根據預設，IntelliSense 完成只會從程式庫顯示已匯入專案的完成項目。 例如，如果您未透過 `using` 匯入 `System.Collections.Generic`，則不會有 `List<>` 的完成項目。 若要從程式庫顯示未匯入的完成項目，則您必須在 Visual Studio for Mac 的 [喜好設定] 中啟用 [Show Import Items] \(顯示匯入項目\)  。 您可以在 [喜好設定] > [文字編輯器] > [IntelliSense]  中找到此設定：

![IntelliSense 的 [Show Import Items] \(顯示匯入項目\)](media/intellisense-showimport.png)

一旦啟用 [Show Import Items] \(顯示匯入項目\)  ，完成清單就會包含您尚未匯入的完成項目。 選取對應至未宣告程式庫的項目時，該程式庫的 `using` 陳述式會自動新增至程式碼檔案的標頭。 完成項目所屬的程式庫名稱也會與完成項目本身一併列出。

![顯示匯入項目清單](media/intellisense-importaction.png)

## <a name="parameter-window"></a>參數視窗

IntelliSense 的另一項功能是能夠在適當的情況下提供參數清單。 參數清單提供所呼叫程式碼的方法簽章詳細資料。 藉由按一下簽章內的向上/向下箭號，即可循環檢視每個可用參數簽章，以判斷最適合您需求的簽章。 除了允許的資料類型詳細資料之外，也可能會有透過 XML 註解在目標方法中定義的描述。

![參數清單](media/intellisense-parameter.png)

當您填入參數時，您目前編輯的參數會是粗體，而非使用中參數則具有標準字型粗細。 


## <a name="triggering-completion-window-and-parameter-window"></a>觸發完成視窗和參數視窗

當您在原始程式檔中鍵入時，就會自動觸發完成視窗。 不過，您也可以使用快速鍵 `control-space` 來觸發完成視窗。 此按鍵組合會使完成清單出現在插入號的目前位置。 

您也可以按下 `control-shift-space` 來手動觸發參數視窗的外觀。 當您的插入號位於對參數清單有效位置時，參數清單會出現在插入號位置附近。

## <a name="see-also"></a>另請參閱

- [快速動作 (Windows 上的 Visual Studio)](/visualstudio/ide/quick-actions)
- [重構程式碼 (Windows 上的 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
