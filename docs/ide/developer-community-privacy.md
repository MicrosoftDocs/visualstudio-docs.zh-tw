---
title: 問題報表的私用資料
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09f3e5fed93cac3a251e4b7cdcaa988e63ff8741
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596264"
---
# <a name="developer-community-data-privacy"></a>開發人員社群資料隱私權

根據預設，[開發人員社群](https://developercommunity.visualstudio.com/)上問題報表中的所有資訊 (包括任何留言和回覆) 都會公開顯示。 這是一項優點，因為它可讓整個社群查看問題、解決方案和其他使用者找到的因應措施。 不過，如果您擔心資料或身分的隱私權，則有下列選項可供選擇。

## <a name="identity-privacy"></a>身分隱私權

如果您擔心揭露您的身分，請[建立新的 Microsoft 帳戶](https://signup.live.com/)，這不會揭露關於您的任何詳細資料。 使用此帳戶來建立您的報表。

## <a name="data-privacy"></a>資料隱私性

如果您擔心資料隱私權，請不要在一律公開的初始報表標題或內容中放置您想要保持私用的任何項目。 相反地，請建立報表，然後注意您會在個別的留言中私下傳送詳細資料。 建立問題報表後，您就能夠指定誰可以查看回覆和附件：

1. 在建立的報表中，選擇 [新增留言] 來建立您對問題的私人描述。

2. 在回覆編輯器中，使用 [提交] 和 [取消] 按鈕下方的控制項來指定回覆的對象。 選擇 [可供仲裁者和原始貼文者檢視] 來限制 Microsoft 員工和您自己的可見性。

   ![開發人員社群的隱私權控制](media/developer-community-privacy-control.png)

   只有您指定的人員才能看到留言以及其中包含的任何影像、連結或程式碼。 留言下的任何回覆具有與原始留言相同的可見性。 即使回覆的私用控制項未正確顯示受限的可見性狀態也是如此。

3. 新增描述，以及重現所需的任何其他資訊、影像和檔案附件。 選擇 [送出] 按鈕以私下傳送這些資訊。

   > [!NOTE]
   > 附加的檔案有 2-GB 的限制，最多 10 個檔案。 如果您需要上傳較大的檔案，則可以提交新的問題報表，或在私用留言中向 Microsoft 員工要求上傳 URL。

若要維護您的隱私權，並讓機密資訊不要公開檢視，請小心地將所有與 Microsoft 的互動保持在這個可見性受限的留言下回覆。 對其他留言的回覆可能會導致您不小心公開機密資訊。

## <a name="data-we-collect"></a>我們收集的資料

如果從 Visual Studio 安裝程式起始 [回報問題]，我們會收集最新的安裝程式記錄檔。

如果從 Visual Studio 中起始 [回報問題]，我們會收集一或多項下列類型的資料：

- 事件記錄檔中的 Watson 和 .NET 項目

- Visual Studio 記憶體內部活動記錄檔

- 若啟用 Watson 集合，則為 PerfWatson 檔案

- LiveShare 記錄檔 (若存在)

- Xamarin 記錄檔 (若存在)

- Nuget 記錄檔 (若存在)

- Web 偵錯工具記錄檔 (若存在)

- 服務中樞記錄和 MEF 錯誤記錄 (若存在)

- Python 記錄 (若存在)

- Windows Forms 記錄（如果有的話）

- 螢幕擷取畫面 (若您選擇包含它的話)

- 記錄資料 (若您選擇要包含記錄的話)，其中包括：

  - 重現問題的步驟

  - ETL 追蹤檔案

  - 傾印檔案

> [!NOTE]
> 只有當您透過提交內含的問題報告來提供許可權時，才會將記錄檔、螢幕擷取畫面和記錄資料傳送至 Microsoft。 您可以看到哪些檔案包含在 [回報問題] 視窗的 [摘要] 步驟中（請參閱此附注中包含的螢幕擷取畫面）。 收集的記錄檔和檔案會儲存在% temp% 資料夾中，並且會在每次上傳後定期清除。 如果您不想要在問題報告中包含記錄檔，請先從% temp% 資料夾中刪除檔案，然後再提交報告。
  > ![回報問題-收集的記錄摘要](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>請參閱

- [如何回報 Visual Studio 的問題](how-to-report-a-problem-with-visual-studio.md)
- [C++ 問題報表的資料隱私權](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
