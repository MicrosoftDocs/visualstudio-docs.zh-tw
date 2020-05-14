---
title: IntelliSense
description: 在 Visual Studio for Mac 中使用 IntelliSense 的資訊
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405812"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense 提供數個功能，可協助增強撰寫和編輯程式碼的體驗。 例如，除了程式碼完成之外，IntelliSense 引擎也提供成員清單、參數資訊和快速諮詢。

在 Visual Studio for Mac 中，IntelliSense 是由核心編輯器服務提供，且支援多種語言，例如 C#、XAML、F#、JavaScript 等。 Visual Studio for Mac 也提供進階 IntelliSense 功能，例如能夠從程式庫顯示尚未匯入專案的完成項目。

## <a name="code-completion"></a>程式碼完成

在支援的檔案 (例如 C# 程式碼檔案) 中鍵入時，會在完成清單中顯示對您目前鍵入字串有效的完成項目，並隨著您鍵入的內容進行更新。 此外，如果您刪除文字，此清單會再次自動更新，以包含完成指定字串的更多可能性。 

完成視窗也支援依類型篩選包含的完成項目。 例如，您可以限制清單的成員只代表類型 (如類別或委派)。 您可以透過按一下代表所要篩選類型的特定圖示，或經由對應於指定類型的鍵盤快速鍵來啟用此篩選程序。 這些圖示位於完成視窗的底部，如下所示：

| 圖示                         | 名稱          | 關鍵字    | 熱鍵 |
| -----------------------------|---------------| -----------|--------|
| ![類別圖示](media/classes-icon.png)  | class         | `class`    |  ⌥C
| ![常數圖示](media/constant-icon.png) | 常數      | `const`    |  ⌥O
| ![委派圖示](media/delegate-icon.png) | 委派      | `delegate` |  ⌥D
| ![列舉圖示](media/enums-icon.png)    | 列舉          | `enum`     |  ⌥E
| ![事件圖示](media/event-icon.png)    | event         |            |  ⌥V
| ![欄位圖示](media/fields-icon.png)   | field         |            |  ⌥F
| ![介面圖示](media/interface-icon.png)| 介面     | `interface`|  ⌥I
| ![關鍵字圖示](media/keyword-icon.png)  | 關鍵字 (keyword)       |            |  ⌥K
| ![方法圖示](media/method-icon.png)   | method        |            |  ⌥M
| ![命名空間圖示](media/namespace-icon.png)| 命名空間     | `namespace`|  ⌥N
| ![屬性圖示](media/props-icon.png)    | 屬性      |            |  ⌥P
| ![程式碼片段圖示](media/snippet-icon.png)  | 程式碼片段       | `class`    |  ⌥S
| ![結構圖示](media/struct-icon.png)   | structure     | `struct`   |  ⌥S

藉由按一下任何圖示，或是按下對應的快速鍵，完成清單就會僅限於篩選集所定義的類型。  

![Intellisense 類型篩選](media/intellisense-typefiltering.gif)

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
