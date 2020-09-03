---
title: 自訂 Visual Studio 2015 如何建立資料繫結控制項的標題 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476924"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自訂 Visual Studio 為資料繫結的控制項建立標題的方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您從 [ [資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) 將專案拖曳到 Windows Form 設計工具時，有一項特殊的考慮：當發現兩個或多個單字要串連在一起時，標題標籤中的資料行名稱會重新格式化為更容易讀取的字串。 您可以在**HKEY_CURRENT_USER \software\microsoft\visualstudio\10.0\data** designer 登錄機碼中設定**SmartCaptionExpression**、 **SmartCaptionReplacement**和**SmartCaptionSuffix**值，以自訂建立這些標籤的方式。

> [!NOTE]
> 在您建立此登錄機碼之前，此登錄機碼不存在。

 智慧型字幕是由輸入至 **SmartCaptionExpression** 值值的正則運算式所控制。 新增 **資料設計** 工具登錄機碼會覆寫控制標題標籤的預設正則運算式。 如需正則運算式的詳細資訊，請參閱 [在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)。

 下表說明控制標題標籤的登錄值。

|登錄專案|描述|
|-------------------|-----------------|
|**SmartCaptionExpression**|用來符合您模式的正則運算式。|
|**SmartCaptionReplacement**|顯示 **SmartCaptionExpression**中相符之任何群組的格式。|
|**SmartCaptionSuffix**|要附加至標題結尾的選擇性字串。|

 下表列出這些登錄值的內部預設設定。

|登錄專案|預設值|說明|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**| (\\ \p{Ll} ) # B2 \\ \p{Lu} ) # A0_ +|符合小寫字元，後面接著大寫字元或底線。|
|**SmartCaptionReplacement**|$1 $2|$1 代表運算式的第一個括弧中相符的任何字元，而 $2 則代表第二個括弧中相符的任何字元。 取代為第一個相符項、一個空格，然後是第二個相符項。|
|**SmartCaptionSuffix**|:|表示附加至傳回之字串的字元。 例如，如果標題為 `Company Name` ，則尾碼會使其成為 `Company Name:`|

> [!CAUTION]
> 在登錄編輯程式中執行任何作業時，應該非常小心。 請先備份登錄再進行編輯。 如果您不正確地使用登錄編輯程式，可能會導致嚴重問題，而需要重新安裝作業系統。 Microsoft 不保證可以解決您使用登錄編輯程式所造成的問題。 您需自行承擔使用登錄編輯程式的風險。

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>修改 [資料來源] 視窗的智慧字幕行為

1. 按一下 [ **開始** ]，然後按一下 [ **執行**]，以開啟命令視窗。

2. `regedit`在 [**執行**] 對話方塊中輸入，然後按一下 **[確定]**。

3. 展開 **HKEY_CURRENT_USER** 節點。

4. 展開 [ **軟體** ] 節點。

5. 展開 **Microsoft** 節點。

6. 展開 [ **VisualStudio** ] 節點。

7. 以滑鼠右鍵按一下 **10.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

8. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionExpression` 。

9. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionReplacement` 。

10. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionSuffix` 。

11. 以滑鼠右鍵按一下 [ **SmartCaptionExpression** ] 專案，然後選取 [ **修改**]。

12. 輸入您想要讓 [ **資料來源** ] 視窗使用的正則運算式。

13. 以滑鼠右鍵按一下 [ **SmartCaptionReplacement** ] 專案，然後選取 [ **修改**]。

14. 輸入以您要顯示正則運算式中符合之模式的格式取代字串。

15. 以滑鼠右鍵按一下 [ **SmartCaptionSuffix** ] 專案，然後選取 [ **修改**]。

16. 輸入您想要出現在標題結尾的任何字元。

     下次當您從 [ **資料來源** ] 視窗拖曳專案時，就會使用提供的新登錄值來建立標題標籤。

### <a name="to-turn-off-the-smart-captioning-feature"></a>關閉 smart 字幕功能

1. 按一下 [ **開始** ]，然後按一下 [ **執行**]，以開啟命令視窗。

2. `regedit`在 [**執行**] 對話方塊中輸入，然後按一下 **[確定]**。

3. 展開 **HKEY_CURRENT_USER** 節點。

4. 展開 [ **軟體** ] 節點。

5. 展開 **Microsoft** 節點。

6. 展開 [ **VisualStudio** ] 節點。

7. 以滑鼠右鍵按一下 **10.0** 節點，然後建立名為的新機 **碼** `Data Designers` 。

8. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionExpression` 。

9. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionReplacement` 。

10. 以滑鼠右鍵按一下 [ **資料設計** 工具] 節點，然後建立名為的新 **字串值** `SmartCaptionSuffix` 。

11. 以滑鼠右鍵按一下 [ **SmartCaptionExpression** ] 專案，然後選取 [ **修改**]。

12. 輸入 `(.*)` 值。 這會與整個字串相符。

13. 以滑鼠右鍵按一下 [ **SmartCaptionReplacement** ] 專案，然後選取 [ **修改**]。

14. 輸入 `$1` 值。 這會將字串取代為相符的值，這是整個字串，因此它會維持不變。

     下次當您從 [ **資料來源** ] 視窗拖曳專案時，標題標籤會以未修改的標題建立。

## <a name="see-also"></a>另請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
