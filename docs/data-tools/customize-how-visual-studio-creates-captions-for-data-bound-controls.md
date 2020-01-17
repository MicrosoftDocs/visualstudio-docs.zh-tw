---
title: 自訂資料繫結控制項的標題
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7780cfb3b266de6f477e74d1b352cf6b24aab42
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113668"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自訂 Visual Studio 為資料繫結的控制項建立標題的方式

當您從 [[資料來源] 視窗](add-new-data-sources.md#data-sources-window)將專案拖曳至設計工具時，會有一項特殊考慮：當發現兩個或多個文字要串連在一起時，標題標籤中的資料行名稱會重新格式化為更容易閱讀的字串。

::: moniker range="vs-2017"

您可以在**HKEY_CURRENT_USER \software\microsoft\visualstudio\15.0\data** designer 登錄機碼中設定**SmartCaptionExpression**、 **SmartCaptionReplacement**和**SmartCaptionSuffix**值，以自訂這些標籤的建立方式。

::: moniker-end

::: moniker range=">=vs-2019"

您可以在**HKEY_CURRENT_USER \software\microsoft\visualstudio\16.0\data** designer 登錄機碼中設定**SmartCaptionExpression**、 **SmartCaptionReplacement**和**SmartCaptionSuffix**值，以自訂這些標籤的建立方式。

::: moniker-end

> [!NOTE]
> 在您建立此登錄機碼之前，此登錄機碼不存在。

智慧標題是由輸入至**SmartCaptionExpression**值值的正則運算式所控制。 加入**資料設計**工具登錄機碼會覆寫控制標題標籤的預設正則運算式。 如需正則運算式的詳細資訊，請參閱[在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

下表描述控制標題標籤的登錄值。

|登錄專案|描述|
|-------------------|-----------------|
|**SmartCaptionExpression**|您用來比對模式的正則運算式。|
|**SmartCaptionReplacement**|要顯示在**SmartCaptionExpression**中符合之任何群組的格式。|
|**SmartCaptionSuffix**|要附加至標題結尾的選擇性字串。|

下表列出這些登錄值的內部預設設定。

|登錄專案|預設值|說明|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|符合小寫字元，後面接著大寫字元或底線。|
|**SmartCaptionReplacement**|**$1 $2**|**$1**代表運算式的第一個括弧中符合的任何字元，而 **$2**則代表在第二個括弧中相符的任何字元。 取代是第一個相符的、一個空格，然後是第二個相符的。|
|**SmartCaptionSuffix**|**:**|表示附加至傳回字串的字元。 例如，如果標題為 `Company Name`，則尾碼會使其 `Company Name:`|

> [!CAUTION]
> 在登錄編輯程式中執行任何動作時，請務必小心。 在編輯登錄之前，請先備份登錄。 如果您不正確地使用登錄編輯程式，可能會導致嚴重問題，而需要重新安裝作業系統。 Microsoft 不保證可以解決使用登錄編輯程式所造成的問題。 您必須自行承擔使用登錄編輯器的風險。
>
> 如需備份、編輯和還原登錄的詳細資訊，請參閱[advanced users 的 Windows 登錄資訊](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)。

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>修改 [資料來源] 視窗的智慧標題列為

1. 依序按一下 [**開始**] 和 [**執行**]，以開啟命令視窗。

2. 在 [**執行**] 對話方塊中輸入 `regedit`，然後按一下 **[確定]** 。

3. 展開 [ **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio** ] 節點。

::: moniker range="vs-2017"

4. 以滑鼠右鍵按一下 [ **15.0** ] 節點，然後建立名為 `Data Designers`的新機**碼**。

::: moniker-end

::: moniker range=">=vs-2019"

4. 以滑鼠右鍵按一下 [ **16.0** ] 節點，然後建立名為 `Data Designers`的新機**碼**。

::: moniker-end

5. 以滑鼠右鍵按一下 [**資料設計**工具] 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 以滑鼠右鍵按一下**SmartCaptionExpression**值，然後選取 [**修改**]。

7. 輸入要讓 [**資料來源**] 視窗使用的正則運算式。

8. 以滑鼠右鍵按一下**SmartCaptionReplacement**值，然後選取 [**修改**]。

9. 以您想要在正則運算式中顯示相符模式的方式，輸入已格式化的取代字串。

10. 以滑鼠右鍵按一下**SmartCaptionSuffix**值，然後選取 [**修改**]。

11. 輸入您想要在標題結尾處顯示的任何字元。

    下次您從 [**資料來源**] 視窗拖曳專案時，會使用所提供的新登錄值來建立標題標籤。

## <a name="turn-off-the-smart-captioning-feature"></a>關閉智慧標題功能

1. 依序按一下 [**開始**] 和 [**執行**]，以開啟命令視窗。

2. 在 [**執行**] 對話方塊中輸入 `regedit`，然後按一下 **[確定]** 。

3. 展開 [ **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio** ] 節點。

::: moniker range="vs-2017"

4. 以滑鼠右鍵按一下 [ **15.0** ] 節點，然後建立名為 `Data Designers`的新機**碼**。

::: moniker-end

::: moniker range=">=vs-2019"

4. 以滑鼠右鍵按一下 [ **16.0** ] 節點，然後建立名為 `Data Designers`的新機**碼**。

::: moniker-end

5. 以滑鼠右鍵按一下 [**資料設計**工具] 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 以滑鼠右鍵按一下**SmartCaptionExpression**專案，然後選取 [**修改**]。

7. 輸入值 `(.*)`。 這會符合整個字串。

8. 以滑鼠右鍵按一下**SmartCaptionReplacement**專案，然後選取 [**修改**]。

9. 輸入值 `$1`。 這會將字串取代為符合的值，這是整個字串，因此它會維持不變。

    下次您從 [**資料來源**] 視窗拖曳專案時，會使用未修改的標題來建立標題標籤。

## <a name="see-also"></a>請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
