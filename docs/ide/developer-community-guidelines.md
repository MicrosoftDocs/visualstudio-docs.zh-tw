---
title: 開發人員社群指導方針
description: 描述使用 Visual Studio 開發人員社群的指導方針。
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0722716b086877d5522b9ef8fae79976fbdb0805
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894669"
---
# <a name="developer-community-guidelines"></a>開發人員社群指導方針

開發人員社群會追蹤 Visual Studio 的問題和功能建議。

## <a name="submitting-problems-and-suggestions"></a>提交問題和建議

[Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)會追蹤 Visual Studio 的問題和功能建議。

### <a name="before-submitting-an-issue"></a>提交問題之前

請在 Visual Studio 開發人員社群上搜尋您的問題，以確定它還不存在。 如果您發現您的問題已存在，請建立相關的批註並轉換投票。

如果您的問題是問題，請使用 _visual studio_ 的標記要求 [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest)的社區。 我們有客戶支援人員監視該標籤，並可協助回答問題。

如果您找不到描述 bug 或功能的現有問題，請使用下列指導方針來提交問題。

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>撰寫良好的錯誤報表或功能建議

- 只針對每個問題提出一個問題或功能要求。

  - 將多個問題或功能要求合併成單一問題，讓我們更難進行診斷，並讓其他使用者更難針對您的問題進行投票。
  - 除非您的問題來自相同的輸入，否則不要將該問題當成現有問題的註解來新增。 許多問題看起來很類似，但有不同的原因，這會讓我們難以診斷您的問題。

- 您可以提供更多的資訊，讓我們能夠更輕鬆地重現並修正您的問題。
- 每個問題都包含下列步驟。

  - 可重現步驟 (1 .。。2 ... 3 ... ) 以及您預期的內容與您所遇到的結果。
  - 影像、動畫或影片的連結。 影像和動畫會說明重現步驟，但 _不_ 會取代它們。
  - 適當的程式碼片段會示範問題或程式碼存放庫的連結，因此我們可以輕鬆地向下提取到我們的電腦以重新建立問題。

- 請記得執行下列步驟：

  - 搜尋以查看是否有重複的。 如果是的話，請將現有的問題投票，視需要提供其他批註或說明。
  - 停用所有擴充功能之後，請重新建立問題。 如果您發現問題是您已安裝的擴充功能所造成，請分別在擴充功能上提出問題。
  - 簡化靠近問題的程式碼，以便讓問題能夠浮現出來。

即使有包括豐富詳細資料的問題，我們也可能無法重現問題，並可能會詢問詳細資訊！

## <a name="managing-problem-reports"></a>管理問題報告

將問題分類是一種在功能小組內共同完成的多步驟流程。 分級通常需要一周，但可能需要較長的時間。 分級的目標是讓您清楚瞭解您的問題會發生什麼事。 例如，在分級之後，您知道我們是否打算修正您的問題，或等候更多的社區意見反應。

回報問題之後，狀態會指出您的提交內容在其生命週期的位置。 當 Visual Studio 產品團隊審視您的意見反應時，他們會以適當的狀態進行設定。 藉由參考 [問題狀態和常見問題](./report-a-problem.md)來追蹤問題報告的進度。

### <a name="prioritizing-which-issues-to-fix"></a>排定要修正問題的優先順序

我們無法修正所有回報的問題。 修正程式太昂貴，有些可能會回歸其他功能區，有些則可能造成影響太低。 如果您已花時間將問題報告傳送給我們，我們瞭解這可能會令人失望。 無論是在此專案中，還是我們所貢獻的其他專案。 如果問題已關閉，而您覺得我們提供的原因不符合，您可以明確地瞭解您的使用案例，並要求重新開機此問題以進行另一次傳遞。 到目前為止，我們可能會要求您提供進一步的資訊。

### <a name="missing-important-information"></a>遺漏重要資訊

當問題遺失重要資訊時，我們會指派 _需要更多的資訊_ 狀態。 我們會根據所需的特定資訊對問題進行批註，而您將會收到電子郵件通知。 如果我們未在七天內收到資訊，則會傳送提醒給您。 之後，我們會在閒置14天之後關閉票證。

### <a name="other-product"></a>其他產品

有時，在報告問題時，會導致另一個產品而不 Visual Studio 的結果。 它可能是另一個相關的應用程式或延伸模組。 

發生這種情況時，我們會關閉問題，並要求您使用其他產品來開啟它。 以下是提出這些問題的一些常見位置：

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio 訂用帳戶支援](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>其他資訊

- [如何提高修正效能問題的機會](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [疑難排解及建立 MSBuild 問題的記錄檔](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>管理功能建議

功能建議是美國與開發人員群體成員之間的通訊方式。 技術上來說，我們可以永遠保持所有功能要求的開啟。 但將問題保持在開啟狀態，可減少社區對功能實際狀態的可見度。 因此，我們會關閉我們不會處理的功能要求，並將我們可能會處理的功能指派給 [ _評論_ ] 標籤。

如果您建議某項功能，可能會因為不打算處理您的要求而感到失望。 我們瞭解。 所有人都已在此專案中，或我們所貢獻的其他專案。 因此，請放心，我們會喜歡您所有的輸入。 當我們關閉或將 [ _審核_ ] 標籤指派給您的建議時，請勿採取個人犯罪。 如果您認為您的功能建議必須保持開啟狀態，請澄清您的使用案例，並與我們聯繫或收集更多投票。

在我們的決策過程中，我們會查看有關功能建議的下列特性：

- 它符合我們的一般產品方向嗎？
- 我們可以承受建立和維護嗎？
- 它是否與我們的整體 [藍圖](/visualstudio/productinfo/vs-roadmap) 策略一致？
- 它是否有依投票和留言指出的社區支援？
- 我們喜歡它，即使是低群支援也是一樣？

當我們無法回答「是」這些問題時，我們會將其關閉。 但是，建議通常會保持開啟狀態 _，以供您_ 收集更多的社區意見反應。

如果建議不符合我們的整體產品方向，我們會將其關閉為 *超出範圍*。 例如，在 Visual Studio 系列產品的其他成員中，我們可能會有類似的投資。 或者，建議的功能可能只與少數人員相關，讓擴充功能更適合提供。

藉由參考 [建議狀態和常見問題](./report-a-problem.md)來追蹤功能建議的進度。

## <a name="discussion-etiquette"></a>討論禮儀

若要讓對話保持清楚且透明，請將討論範圍限制為英文，並保留與問題相關的事項。 明智給其他人，並一律嘗試不致和 professional。

如需詳細資訊，請參閱 [Microsoft 社區](https://answers.microsoft.com/en-us/page/codeofconduct)管理辦法。

任何對討論禮儀的違規可能會導致移除批註，最後禁用使用者。

## <a name="data-privacy"></a>資料隱私權

批註和回復都是公開可見的，但任何附加的檔案都只會與 Microsoft 私下共用。 此可見度很有説明，因為它可讓整個團體查看其他使用者所找到的問題和解決方案。 如果您擔心資料或身分識別的隱私權，則有選項。 深入瞭解 [開發人員社群資料隱私權](./developer-community-privacy.md)。

## <a name="next-steps"></a>下一步

請前往 [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8) 來回報問題、建議功能，或流覽現有的票證。 盡情享受！
