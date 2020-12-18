---
title: 如何回報 Visual Studio 的問題
description: 了解如何回報 Visual Studio 的問題
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c6c09bbf74cca803156842d185b5bf86ff52439
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668816"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>如何回報 Visual Studio 或 Visual Studio 安裝程式的問題

> [!NOTE]
> 針對 Visual Studio for Mac，請參閱[如何在 Visual Studio for Mac 中回報問題](/visualstudio/mac/report-a-problem)。

您可以從 Visual Studio 或其安裝程式報告問題。 內建的意見反應工具可讓您輕鬆地新增診斷資訊，以協助 Visual Studio 小組診斷和修正問題。 以下是回報問題的步驟。

1. **在 Visual Studio 中**，選取右上角的意見反應圖示，然後選取 [回報問題]。 您也可以從功能表中存取意見反應工具，**協助**  >  **傳送意見** 反應回報  >  **問題**。
![Visual Studio 開發人員社群上的回報問題彈出視窗](media/feedback-button.png) 如果您無法安裝 Visual Studio 或無法在 Visual Studio 中存取意見反應工具，您也可以改為在 **Visual Studio 安裝程式** 中回報問題。  在安裝程式中，選取右上角的意見反應圖示，然後選取 [回報問題]。
![在安裝程式的 Visual Studio 開發人員社群報告問題快顯視窗](media/installer.png)

1. 按一下 [回報 **問題** ] 會開啟您的預設瀏覽器，並使用您用來登入的相同帳戶將您登入 Visual Studio

   ![登入以回報問題](../ide/media/feedback-browser-top.png)

1. 一開始請輸入您 bug 報告的描述性標題。 長度至少必須有25個字元。

    ![回報問題](../ide/media/feedback-report.png)

1. 當您開始輸入時，[標題] 欄位底下會顯示可能的重複專案

    ![搜尋重複專案](../ide/media/feedback-search.png)

1. 選取可能的重複錯誤報表，以查看是否有一個符合您自己的問題。 如果有，請投票給它，而不是建立您自己的票證。

    ![投票重複專案](../ide/media/feedback-duplicate.png)

2. 如果找不到任何重複專案，請輸入問題的描述以繼續。 請務必盡可能清楚地提高我們能夠重現 bug 的機會。 請務必包含明確的重現步驟。

3. 如果與 bug 報告相關，請選取 [ *包含 Visual Studio 螢幕擷取畫面* ] 核取方塊來取得螢幕擷取畫面。

    ![](../ide/media/feedback-screenshot.png)*只需要 Microsoft 工程師可以看到螢幕擷取畫面*

    您甚至可以直接在瀏覽器中裁剪螢幕擷取畫面，以移除任何敏感性或不相關的部分。

4. 協助 Visual Studio 工程團隊解決問題的其中一種最佳方式，就是提供追蹤和堆積傾印檔案供他們查看。 您可以藉由記錄導致錯誤的步驟來輕鬆執行此動作。

    ![只記錄您 ](../ide/media/feedback-recording.png) *的動作 Microsoft 工程師可以看到記錄*

5. 如果您認為附加的檔案可協助診斷問題，請檢查這些檔案並上傳其他檔案。

    ![附加 ](../ide/media/feedback-attachments.png) *的檔案只有 Microsoft 工程師可以看到附加的* 檔案

6. 最後一個步驟是按 [ **提交** ] 按鈕。 提交報表會將它直接傳送到內部 Visual Studio bug 報告系統，以等候分級。

## <a name="when-further-information-is-needed"></a>需要進一步的資訊時

當問題遺失重要資訊時，我們會指派 **需要更多的資訊** 狀態。 我們會根據所需的特定資訊對問題進行批註，而您將會收到電子郵件通知。 如果我們未在七天內收到資訊，則會傳送提醒給您。 之後，我們會在閒置14天之後關閉票證。

1. 遵循電子郵件中的連結至問題報告，或移至首頁以查看 [ **需要更多資訊** ] 狀態中的所有報表。

    ![我的意見反應](../ide/media/feedback-my-feedback.png)

1. 選取問題報表上的 [提供詳細資訊] 連結，會將您流覽至新的畫面。 您可以從這裡查看所要求的資訊。

   ![要傳送給 Microsoft 的資訊詳細資料](../ide/media/feedback-need-more-info.png)

1. 您可以藉由新增留言、附件或錄製步驟，來提供更多資訊。 這個體驗類似於在對問題投票時，回報新問題或提供額外資訊。

1. 提出要求的 Microsoft 工程師會收到提供了額外資訊的通知。 如果他們有足夠的資訊可供調查，問題狀態就會變更。 否則，工程師會進一步要求更多資訊。

您可以在 [ **我的意見** 反應] 畫面上查看這些要求，以及所有其他 **問題** 和 **建議**。

## <a name="search-for-solutions-or-provide-feedback"></a>搜尋解決方案或提供意見反應

如果您不想要或無法使用 Visual Studio 來回報問題，有可能那個問題已經回報過，而且解決方案已張貼於 [Visual Studio 開發人員社群頁面](https://developercommunity2.visualstudio.com/search?space=8) \(英文\) 頁面。

如果您沒有要回報的問題，但想要建議某項功能，也有一個地方可以這麼做。 如需詳細資訊，請參閱[提出功能建議](https://aka.ms/feedback/suggest?space=8)頁面。

## <a name="see-also"></a>另請參閱

* [開發人員社群指導方針](./developer-community-guidelines.md)
* [Visual Studio 意見反應選項](../ide/feedback-options.md)
* [報告 Visual Studio for Mac 的問題](/visualstudio/mac/report-a-problem)
* [回報 C++ 的問題](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)
* [開發人員社群資料隱私權](developer-community-privacy.md)
