---
title: 如何回報 Visual Studio 的問題
titleSuffix: ''
description: 了解如何將 Visual Studio 2017 的問題回報給 Microsoft，以便我們可以診斷並修正問題。
ms.date: 03/11/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6225fa70bba0f6b044bb77a83ea03bda34591a41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042643"
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>如何回報 Visual Studio 2017 的問題

如果您在使用 Visual Studio 時發生問題，我們會想要進行了解。 以下說明如何向 [Developer Community](https://developercommunity.visualstudio.com/) 回報問題，讓我們加以診斷及修正。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[如何在 Visual Studio for Mac 中回報問題](/visualstudio/mac/report-a-problem)。

## <a name="report-a-problem-by-using-visual-studio"></a>使用 Visual Studio 回報問題

若要回報 Visual Studio 的問題，您必須從 Visual Studio 或 Visual Studio 安裝程式進行回報。 請勿直接透過 [Developer Community](https://developercommunity.visualstudio.com/) 網站進行。 透過 Visual Studio 回報可讓診斷資訊自動包含在報告中。

![Visual Studio Developer Community 上的回報問題快顯](media/report-an-issue.png)

1. 在 Visual Studio 中，選取 [說明] > [傳送意見反應] > [回報問題]。

   > [!TIP]
   > 若您無法完成 Visual Studio 安裝，或是無法存取 Visual Studio 中的意見反應工具，您可以使用 **Visual Studio 安裝程式**來回報問題。 若要這麼做，請在 **Visual Studio 安裝程式**中選擇右上角的意見反應圖示。

1. 如果您尚未登入，請選取位於工具右邊的 [登入]，如以下螢幕擷取畫面所示。 依照畫面上的指示操作來登入。

   ![登入以回報問題](../ide/media/sign-in-new-ux.png)

   當您登入時，可以回報您遇到的問題。 您也可以在您看到的其他任何問題貼文上投票或留言。

1. 登入後，就能在 [我追蹤的項目] 畫面中看到您的 [問題] 及 [活動]

    ![我追蹤的項目](../ide/media/items-i-follow.png)

1. Visual Studio 提供一個介面，讓您搜尋自己的問題並看看其他人是否已回報過。 如果有人回報過，則請對它投票，讓我們知道。
   > [!NOTE]
   > 若要搜尋，請在搜尋方塊中輸入想要的文字，然後按一下 Enter 或按搜尋圖示。

   ![搜尋類似問題並針對類似問題投票](../ide/media/search-and-vote.png)

1. 若沒有找到您遇到的問題，請選擇畫面底部的 [回報新問題]。

   > [!NOTE]
   > [回報新問題] 按鈕只會顯示在 Visual Studio 的 Developer Community 介面。 您無法直接在 [Developer Community](https://developercommunity.visualstudio.com/) 網站回報問題。

1. 建立問題的描述性標題，如此可協助我們將問題發送給適當的 Visual Studio 團隊。

1. 請提供其他任何詳細資訊給我們，如果可能，也請提供重現問題的步驟。

   ![回報新問題](../ide/media/report-new-problem.png)

1. 選取 [下一步] 移到 [附件] 索引標籤。您可在這裡擷取目前畫面，並傳送給 Microsoft。 若要附加額外的螢幕擷取畫面或其他檔案，請選擇 [附加其他檔案]。

   ![將螢幕擷取畫面附加到 Visual Studio 問題報告](media/report-a-problem-screenshot.png)

1. 若您不想附加螢幕擷取畫面或[錄製重現](#record-a-repro)，請選取 [下一步] 移到 [摘要] 索引標籤。

1. 選取 [提交]，連同任何影像、追蹤檔案或傾印檔案送出您的報表。 (如果 [提交] 按鈕呈現灰色，請確定您已提供報表的標題與描述。)

   如需所收集的資料相關資訊，請參閱[我們收集的資料](developer-community-privacy.md#data-we-collect)。

## <a name="record-a-repro"></a>錄製重現

追蹤和堆積傾印檔案有助於我們診斷問題。 我們很感激您願意使用 [回報問題] 工具記錄重現問題的步驟，並將資料傳送給 Microsoft。 以下是操作說明：

1. 在您輸入問題的標題與描述後，選取 [下一步] 前往 [附件] 索引標籤。

1. 選擇 [錄製] 索引標籤。

1. 在 [錄製您的動作] 下，若您能在目前的 Visual Studio 執行個體重現問題，請加以選取。 若因為 Visual Studio 停止回應等情況而無法這樣做，則選取 [建立新的執行個體>]**\<**，在新的 Visual Studio 執行個體中錄製動作。

1. 選取 [開始錄製]。 授與權限來執行工具。

   ![選擇 [開始錄製] 以在 Visual Studio 問題報告中提供追蹤與堆積傾印檔案](../ide/media/record-dialog-box.png)

1. 出現 [步驟收錄程式] 工具時，請執行重現問題的步驟。

1. 完成之後，請選擇 [停止錄製] 按鈕。

1. 請稍等幾分鐘，讓 Visual Studio 收集和封裝已錄製的資訊。

   如需所收集的資料相關資訊，請參閱[我們收集的資料](developer-community-privacy.md#data-we-collect)。

## <a name="when-further-information-is-needed-need-more-info"></a>需要更多資訊時 (需要更多資訊)

從 Visual Studio 2017 版本 15.5 開始，有新的工作流程可協助使用者提供問題報告的額外資訊。

1. 當 Microsoft 工程師將 [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) 的問題設為**需要更多資訊**狀態時，對問題進行張貼、投票、追蹤或留言的任何使用者，都會在 Visual Studio 中的**回報問題**工具收到通知。

   ![Visual Studio 中需要更多資訊的通知](../ide/media/nmi-notification.png)

1. 按一下 [檢視問題] 連結來篩選及排序檢視，以顯示需要注意的問題。 這些問題旁還會有指標，以在一般搜尋中加以區分。

1. 按一下問題即可看到問題的詳細資料檢視。

   ![需要更多資訊的通知](../ide/media/nmi-details-view.png)

1. 若要檢視**需要更多資訊**要求，請在問題詳細資料檢視中按一下 [檢視他人的要求與回覆] 連結。 對話方塊隨即顯示要求。

   ![需要更多資訊的通知](../ide/media/nmi-request.png)

1. 您可以藉由新增留言、附件或錄製步驟，來提供更多資訊。 這個體驗類似於在對問題投票時，回報新問題或提供額外資訊。

1. 提出要求的 Microsoft 工程師會收到提供了額外資訊的通知。 如果他們有足夠的資訊可供調查，問題狀態就會變更。 否則，工程師會進一步要求更多資訊。

   > [!NOTE]
   > * 當您回覆時，通知就會消失。 在那個位置，您會看到一個橫幅向您致謝，並鼓勵您提供更多資訊。
   > * 一旦問題變更了狀態，追蹤問題的所有人就都不會再看到通知。
   > * 不只一個人可以回覆同一個**需要更多資訊**要求。
   > * 當您從網頁瀏覽器直接存取 [Developer Community](https://developercommunity.visualstudio.com/) 時，上面不會有**需要更多資訊**工作流程，但仍可在該處提供留言和附件。

## <a name="search-for-solutions-or-provide-feedback"></a>搜尋解決方案或提供意見反應

如果您不想要或無法使用 Visual Studio 來回報問題，有可能那個問題已經回報過，而且解決方案已張貼於 [Visual Studio Developer Community 頁面](https://developercommunity.visualstudio.com/)。

如果您沒有要回報的問題，但想要提出功能建議，也有管道可以這樣做。 如需詳細資訊，請參閱[提出功能建議](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)頁面。

## <a name="see-also"></a>另請參閱

* [告訴我們](../ide/talk-to-us.md)
* [回報 Visual Studio for Mac 的問題](/visualstudio/mac/report-a-problem)
* [回報 C++ 的問題](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)
* [Developer Community 資料隱私權](developer-community-privacy.md)