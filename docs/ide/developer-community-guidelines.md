---
title: 開發人員社群指導方針
description: 說明使用 Visual Studio 開發人員社區的指導方針。
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb7f821a7b815b29c9f85b6ab0686edb0292866d
ms.sourcegitcommit: 4d5cd0b9de7a87efb69f17b02c2331b749e6ec8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86137562"
---
# <a name="developer-community-guidelines"></a>開發人員社群指導方針

開發人員小組會追蹤 Visual Studio 的問題和功能建議。

## <a name="submitting-problems-and-suggestions"></a>提交問題和建議

[Visual Studio 開發人員社區](https://developercommunity.visualstudio.com/)會追蹤 Visual Studio 的問題和功能建議。

### <a name="before-submitting-an-issue"></a>提交問題之前

請在 Visual Studio 開發人員的論壇上搜尋您的問題，以確保它還不存在。 如果您發現您的問題已存在，請建立相關的批註並轉換投票。

如果您的問題是問題，請使用_visual studio_的標記向[Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest)詢問。 我們有客戶支援人員負責監控該標記，並將協助回答問題。

如果您找不到描述 bug 或功能的現有問題，請使用下列指導方針提交問題。

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>撰寫良好的 bug 報告或功能建議

- 僅針對每個問題提出一個問題或功能要求。

  - 將多個問題或功能要求結合成單一問題，可讓我們更難診斷，而其他使用者則難以投票您的問題。
  - 請不要將您的問題新增為現有問題的批註，除非它是針對相同的輸入。 許多問題看起來都很類似，但有不同的原因，這使得我們難以診斷您的問題。

- 您可以提供的資訊越多，我們就越容易重現並修正您的問題。
- 針對每個問題包含下列步驟。

  - 可重現的步驟（1 .。。2 ... 3 ...）以及您的期望與經驗。
  - 影像、動畫或影片的連結。 影像和動畫會說明重現步驟，但_不_會取代它們。
  - 在適當的情況下，我們可以輕鬆地向下提取問題的程式碼片段，或程式碼存放庫的連結，以重新建立問題。

- 請記得執行下列步驟：

  - 搜尋以查看是否有重複的。 若是如此，請投票現有的問題，並視需要提供其他意見或說明。
  - 停用所有擴充功能之後，請重新建立問題。 如果您發現問題是由已安裝的擴充功能所造成，請分別在此延伸模組上提出問題。
  - 簡化問題的程式碼，讓我們能夠更緊密地找出問題。

即使有包含豐富詳細資料的問題，我們還是無法重現問題，而且可能會要求您提供詳細資訊！

## <a name="managing-problem-reports"></a>管理問題報告

將問題分類是在功能小組中共同完成的多步驟程式。 分類通常需要一周，但可能需要較長的時間。 分級的目標是讓您清楚瞭解您的問題會發生什麼事。 例如，在分級之後，您知道我們是否打算修正您的問題，或等待更多的社區意見反應。

回報問題之後，狀態會指出您的提交內容在其生命週期的位置。 當 Visual Studio 產品小組審查您的意見時，他們會以適當的狀態進行設定。 藉由參考[問題狀態和常見問題，](https://docs.microsoft.com/visualstudio/ide/report-a-problem)追蹤問題報告的進度。

當問題缺少重要資訊時，我們會將 [_需要更多資訊_] 狀態指派給 [其他資訊]。 我們會針對我們所需的特定資訊來留言問題，而且您會收到電子郵件通知。 如果我們在七天內未收到資訊，我們會傳送提醒給您。 之後，我們會在沒有活動14天后關閉票證。

### <a name="wont-fix-bugs"></a>不會修正 bug

當有負面的成本效益餘額時，我們會關閉一些 bug。 例如，如果修正很複雜，it 風險會對許多使用者進行回歸，修正可能不合理。 當我們關閉這類錯誤時，我們會說明為何要這麼做。

### <a name="other-product"></a>其他產品

有時候回報問題的原因是另一項產品，而不是 Visual Studio。 它可以是另一個相關的應用程式或擴充功能。 

發生這種情況時，我們會關閉問題，並要求您將它與其他產品開啟。 以下是一些用來提出這些問題的常見位置：

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio 訂用帳戶支援](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>其他資訊

- [如何增加修正效能問題的機率](https://docs.microsoft.com/visualstudio/ide/how-to-increase-chances-of-performance-issue-being-fixed)
- [疑難排解及建立 MSBuild 問題的記錄檔](https://docs.microsoft.com/visualstudio/ide/msbuild-logs)

## <a name="managing-feature-suggestions"></a>管理功能建議

功能建議是我們與開發人員團體成員之間通訊的一種方法。 就技術上而言，我們可以將所有功能要求永遠保持開啟。 但保持開啟的問題，可以減少對功能的實際狀態的社區可見度。 因此，我們關閉了「功能要求」，我們將不會處理這些功能並將其指派給 [_審查_] 標籤。

如果您建議某項功能，您可能會感到失望，我們不打算處理您的要求。 我們瞭解。 我們已在此專案中，或我們已貢獻的其他人。 因此，請放心，我們喜歡您所有的輸入。 當我們關閉或將 [_審核_] 標籤指派給您的建議時，請勿採取個人違犯。 如果您認為您的功能建議應該保持開啟，請澄清您的使用案例，並洽詢我們，或收集更多投票。

在我們的決策制定程式中，我們會查看下列有關功能建議的特性：

- 我們可以承受建立和維護嗎？
- 它會與我們的整體[藍圖](https://docs.microsoft.com/visualstudio/productinfo/vs-roadmap)策略一致嗎？
- 它是否具有如投票和留言所指示的社區支援？
- 即使有較低的社區支援，我們是否愛用？

當我們無法回答上述任何問題時，我們會將它關閉。 但通常建議會保持開啟_狀態，以_收集更多的社區意見反應。

藉由參考[建議狀態和常見問題](https://docs.microsoft.com/visualstudio/ide/report-a-problem)來追蹤功能建議的進度。

## <a name="discussion-etiquette"></a>討論禮儀

若要保持對話的清晰和透明化，請將討論範圍限制為英文，並保留與問題相關的事項。 明智給其他人，並一律嘗試不致和 professional。

如需詳細資訊，請參閱[Microsoft 社區程式碼](https://answers.microsoft.com/en-us/page/codeofconduct)管理辦法。

對討論禮儀的任何違規，可能會導致移除批註，最後禁用使用者。

## <a name="data-privacy"></a>資料隱私權

批註和回復是公開可見的，但任何附加的檔案只會私下與 Microsoft 共用。 這種可見度很有用，因為它可讓整個社區查看其他使用者所找到的問題和解決方案。 如果您擔心資料或身分識別的隱私權，您可以選擇。 深入瞭解[開發人員社區資料隱私權](https://docs.microsoft.com/visualstudio/ide/developer-community-privacy)。

## <a name="next-steps"></a>後續步驟

前往[Visual Studio 的開發人員社區](https://developercommunity.visualstudio.com/)，以報告問題、建議功能，或流覽現有的票證。 盡情享受！
