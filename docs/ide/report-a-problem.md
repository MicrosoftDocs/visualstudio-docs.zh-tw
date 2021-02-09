---
title: 回報問題：狀態和常見問題
description: 提供 [回報問題] 工具的概觀，並包括問題狀態和定義
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9b012f1e5fda4a8855bfc6215cf3d458037bc036
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878652"
---
# <a name="report-a-problem-states-and-faq"></a>回報問題：狀態和常見問題

[回報問題] 工具可讓 Visual Studio 開發人員社群提交問題。 您的每個問題報表都會變成我們核心工程系統的工作項目，讓您能夠直接與產品小組交流，以協助我們識別及解決有影響的問題。 與豐富診斷資訊一起提交的意見反應，對於改善 Visual Studio 產品系列至關重要。 我們非常感謝您撥冗回報問題。

此外，您可以對其他社群成員的意見反應進行投票，以便更加關注問題並協助更快地進行修正。

## <a name="problem-status"></a>問題狀態

回報問題之後，狀態會指出您的提交內容在其生命週期的位置。 當 Microsoft 小組檢閱您的意見反應時，他們會使用適當的狀態加以設定。  請藉由參考以下列出的狀態，以及其意義和色彩指標來追蹤問題報表的進度。

![問題回報在開發人員社群上的 [新增] 狀態](../ide/media/ProblemStates/New.jpg)

[新增] 表示新回報的 Bug 或問題，而且尚未對其採取任何動作。

- - -

![問題回報在開發人員社群上的 [已分級] 狀態](../ide/media/ProblemStates/Triaged.jpg)

[已分級] 表示已完成初步執行步驟，例如仲裁、轉譯，以及初始檢查重複項目。 您的票證已路由給適當的工程小組以進行考量。

- - -

![問題回報在開發人員社群上的 [考量中] 狀態](../ide/media/ProblemStates/UnderConsideration.jpg)

[考量中] 表示 Microsoft 正在檢閱問題的社群影響，並據以設定其優先順序。 如果社群影響還不明確或不重要，我們將持續監視處於這個狀態的問題。

- - -

![問題回報在開發人員社群上的 [調查中] 狀態](../ide/media/ProblemStates/UnderInvestigation.jpg)

[調查中] 表示工程師正在積極調查您的問題以尋找解決方法。

- - -

![問題回報在開發人員社群上的 [需要更多資訊] 狀態](../ide/media/ProblemStates/NeedMoreInfo.jpg)

[需要更多資訊] 表示我們需要您提供更多診斷資訊，讓我們能夠繼續進行調查。  [了解如何回應「需要更多資訊」要求。](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed)

- - -

![問題回報在開發人員社群上的 [已修正 - 等待發行] 狀態](../ide/media/ProblemStates/FixedPendingRelease.jpg)

[已修正 - 等待發行] 表示我們擁有此問題的修正程式，並且會在即將推出的預覽版或版本中提供。  當修正程式在預覽版中可供使用時，問題會以指定預覽版本的「在...中修正」標籤來進行標記。

- - -

![問題回報在開發人員社群上的 [已關閉 - 已修正] 狀態](../ide/media/ProblemStates/ClosedFixed.jpg)

[已關閉 - 已修正] 表示我們已發行問題的修正程式。 問題現在也會以指定發行版本的「在...中修正」標籤來進行標記。

- - -

![問題回報在開發人員社群上的 [已關閉 - 重複] 狀態](../ide/media/ProblemStates/ClosedDuplicate.jpg)

[已關閉 - 重複]  表示您的問題已透過另一個意見反應回報。 我們將為您提供可在其中追蹤原始問題報表的連結。

- - -

![問題回報在開發人員社群上的 [已關閉 - 優先順序較低] 狀態](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

[已關閉 - 優先順序較低] 為了讓你們每個人在開發人員社群中獲得最大價值，我們會優先考慮具有最高客戶影響的問題。 雖然我們此時無法解決此特定問題，但可保證您的所有意見反應都極具價值並有助於改善 Visual Studio。

- - -

![問題回報在開發人員社群上的 [已關閉 - 不是 Bug] 狀態](../ide/media/ProblemStates/ClosedNotABug.jpg)

[已關閉 - 不是 Bug] 表示我們已判定所回報功能是依照目前設計的結果。

- - -

![問題回報在開發人員社群上的 [已關閉 - 資訊不足] 狀態](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

[已關閉 - 資訊不足] 表示我們沒有足夠的資訊來為您調查此問題。 我們很樂意在取得所需的資訊之後，重新考慮意見反應。

- - -

![問題回報在開發人員社群上的 [已關閉 - 其他產品] 狀態](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

[已關閉 - 其他產品] 表示我們已判定您的問題適用於另一個產品。 如需外部產品及任何相關連結，請參閱 Microsoft 的評論。

- - -

## <a name="faq"></a>常見問題集

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>如何增加我快速解決問題的機率？

建議您使用搜尋來確保您即將回報的問題尚未回報。 如果發現符合您問題的現有項目，請追蹤該問題票證並對其進行投票。

請提供可協助我們小組重現您所遭遇問題的一切資訊。  這項資訊包含所需的重現步驟、程式碼片段、螢幕擷取畫面、重現記錄、記錄檔和其他成品。  以下是[如何在 Visual Studio 中回報問題](./how-to-report-a-problem-with-visual-studio.md)。

### <a name="how-is-my-feedback-prioritized"></a>如何設定意見反應的優先順序？

我們從客戶收到大量的重要問題。 為了確保您們每個人可在開發人員社群中獲得最大價值，我們優先考慮對具有最高社群影響的意見反應採取動作。

如果我們無法親自回應您的意見反應，請了解我們非常感謝您提供意見。 請確定您的所有意見反應都傳達給正確小組。

我們非常感謝您在改善 Visual Studio 所投入的時間。

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>如果我不滿意解決方法，可以採取哪些動作？

我們小組會盡全力診斷及修正您遇到的任何問題，不過有時候您可能對我們的建議不完全滿意。 請在意見反應上留言，讓我們知道您對哪些部分感到不滿意，我們會盡全力確保我們符合您的需求。

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>如何收到有關意見反應進度的通知？

Microsoft 工程小組可在有進展時於意見反應票證上留言並變更您的票證狀態，藉以與您進行通訊。 請監看票證狀態變更或張貼留言時所傳送的電子郵件通知。  您可以在開發人員社群網站的 [設定檔] 和 [喜好設定] 設定中管理通知的頻率。

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>為什麼無法在開發人員社群網站上新增 Visual Studio IDE 的問題？

透過 Visual Studio 回報問題可讓診斷資訊自動包含在報表中。 它可為我們工程師提供完全了解並解決該問題所需內容的基本資訊。

透過 Visual Studio 回報後，您可以輕鬆地與我們分享豐富的診斷資訊，例如大型記錄檔、損毀資訊、螢幕擷取畫面、重現記錄和其他成品，協助我們更快地為您提供高品質的解決方法。
