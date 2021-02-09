---
title: 自訂資料繫結控制項的標題
description: 自訂 Visual Studio 如何建立資料繫結控制項的標題。 修改 [資料來源] 視窗的智慧字幕行為。 關閉智慧字幕。
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: be9a6840c3b41b442e5019e08c4d2f4d2fa5c3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858991"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自訂 Visual Studio 為資料繫結的控制項建立標題的方式

當您從 [ [資料來源] 視窗](add-new-data-sources.md#data-sources-window) 將專案拖曳至設計工具時，會有特殊的考慮：當發現兩個或多個單字要串連在一起時，標題標籤中的資料行名稱會重新格式化為更容易讀取的字串。

::: moniker range="vs-2017"

您可以在 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** 登錄機碼中設定 **SmartCaptionExpression**、 **SmartCaptionReplacement** 和 **SmartCaptionSuffix** 值，以自訂建立這些標籤的方式。

::: moniker-end

::: moniker range=">=vs-2019"

您可以在 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designers** 登錄機碼中設定 **SmartCaptionExpression**、 **SmartCaptionReplacement** 和 **SmartCaptionSuffix** 值，以自訂建立這些標籤的方式。

::: moniker-end

> [!NOTE]
> 在您建立此登錄機碼之前，此登錄機碼不存在。

智慧型字幕是由輸入至 **SmartCaptionExpression** 值值的正則運算式所控制。 新增 **資料設計** 工具登錄機碼會覆寫控制標題標籤的預設正則運算式。 如需正則運算式的詳細資訊，請參閱 [在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

下表說明控制標題標籤的登錄值。

|登錄專案|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|您用來符合模式的正則運算式。|
|**SmartCaptionReplacement**|顯示 **SmartCaptionExpression** 中相符之任何群組的格式。|
|**SmartCaptionSuffix**|要附加至標題結尾的選擇性字串。|

下表列出這些登錄值的內部預設設定。

|登錄專案|預設值|說明|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\ \p{Ll} ) # B2 \\ \p{Lu} ) # A0_ +**|符合小寫字元，後面接著大寫字元或底線。|
|**SmartCaptionReplacement**|**$1 $2**|**$1** 代表運算式的第一個括弧中相符的任何字元，而 **$2** 則代表第二個括弧中相符的任何字元。 取代為第一個相符項、一個空格，然後是第二個相符項。|
|**SmartCaptionSuffix**|**:**|表示附加至傳回之字串的字元。 例如，如果標題為 `Company Name` ，則尾碼會使其成為 `Company Name:`|

> [!CAUTION]
> 在登錄編輯程式中執行任何作業時，請務必小心。 請先備份登錄再進行編輯。 如果您不正確地使用登錄編輯程式，可能會導致嚴重問題，而需要重新安裝作業系統。 Microsoft 不保證可以解決您使用登錄編輯程式所造成的問題。 您需自行承擔使用登錄編輯程式的風險。
>
> 如需有關備份、編輯和還原登錄的詳細資訊，請參閱 [advanced users 的 Windows 登錄資訊](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)。

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>修改 [資料來源] 視窗的智慧字幕行為

1. 按一下 [ **開始** ]，然後按一下 [ **執行**]，以開啟命令視窗。

2. `regedit`在 [**執行**] 對話方塊中輸入，然後按一下 **[確定]**。

3. 展開 [ **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** ] 節點。

::: moniker range="vs-2017"

4. 以滑鼠右鍵按一下 **15.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

::: moniker-end

::: moniker range=">=vs-2019"

4. 以滑鼠右鍵按一下 **16.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

::: moniker-end

5. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 以滑鼠右鍵按一下 **SmartCaptionExpression** 值，然後選取 [ **修改**]。

7. 輸入您想要讓 [ **資料來源** ] 視窗使用的正則運算式。

8. 以滑鼠右鍵按一下 **SmartCaptionReplacement** 值，然後選取 [ **修改**]。

9. 輸入以您要顯示正則運算式中符合之模式的格式取代字串。

10. 以滑鼠右鍵按一下 **SmartCaptionSuffix** 值，然後選取 [ **修改**]。

11. 輸入您想要出現在標題結尾的任何字元。

    下次當您從 [ **資料來源** ] 視窗拖曳專案時，就會使用提供的新登錄值來建立標題標籤。

## <a name="turn-off-the-smart-captioning-feature"></a>關閉 smart 字幕功能

1. 按一下 [ **開始** ]，然後按一下 [ **執行**]，以開啟命令視窗。

2. `regedit`在 [**執行**] 對話方塊中輸入，然後按一下 **[確定]**。

3. 展開 [ **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** ] 節點。

::: moniker range="vs-2017"

4. 以滑鼠右鍵按一下 **15.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

::: moniker-end

::: moniker range=">=vs-2019"

4. 以滑鼠右鍵按一下 **16.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

::: moniker-end

5. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 以滑鼠右鍵按一下 [ **SmartCaptionExpression** ] 專案，然後選取 [ **修改**]。

7. 輸入 `(.*)` 值。 這會與整個字串相符。

8. 以滑鼠右鍵按一下 [ **SmartCaptionReplacement** ] 專案，然後選取 [ **修改**]。

9. 輸入 `$1` 值。 這會將字串取代為相符的值，這是整個字串，因此它會維持不變。

    下次當您從 [ **資料來源** ] 視窗拖曳專案時，標題標籤會以未修改的標題建立。

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
