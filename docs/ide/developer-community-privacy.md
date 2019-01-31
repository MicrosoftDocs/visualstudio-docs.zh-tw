---
title: 問題報表的私用資料
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ac5c42f91e7dbf4dac310d67fc710f75fc8309
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986848"
---
# <a name="developer-community-data-privacy"></a>開發人員社群資料隱私權

根據預設，[開發人員社群](https://developercommunity.visualstudio.com/)上問題報表中的所有資訊 (包括任何留言和回覆) 都會公開顯示。 這是一項優點，因為它可讓整個社群查看問題、解決方案和其他使用者找到的因應措施。 不過，如果您擔心資料或身分的隱私權，則有下列選項可供選擇。

## <a name="identity-privacy"></a>身分隱私權

如果您擔心揭露您的身分，請[建立新的 Microsoft 帳戶](https://signup.live.com/)，這不會揭露關於您的任何詳細資料。 使用此帳戶來建立您的報表。

## <a name="data-privacy"></a>資料隱私權

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

- *VSFeedbackPerfWatsonData* 資料夾中的 PerfWatson 檔案 (若已啟用 Watson 收集的話)

- *VSFeedbackVSRTCLogs* 資料夾中的 LiveShare 記錄檔 (若存在的話)

- *%LOCALAPPDATA%\Xamarin\Logs* 中的 Xamarin 記錄檔 (若存在的話)

- *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg* 中的 Nuget 記錄檔 (若存在的話)

- Web 偵錯工具記錄檔 (若存在的話)：

   - *%TEMP%\vscode-chrome-debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-edge-debug.txt*

- 螢幕擷取畫面 (若您選擇包含它的話)

- 記錄資料 (若您選擇要包含記錄的話)，其中包括：

   - 重現問題的步驟

   - ETL 追蹤檔案

   - 傾印檔案

    > [!NOTE]
    > 您可以刪除任何不想在提交報表之前提交的記錄資料。

## <a name="see-also"></a>另請參閱

- [如何回報 Visual Studio 的問題](how-to-report-a-problem-with-visual-studio-2017.md)
- [C++ 問題報表的資料隱私權](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)