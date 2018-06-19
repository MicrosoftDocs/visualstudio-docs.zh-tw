---
title: 如何：檢視、儲存和設定組建記錄檔 | Microsoft Docs
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1888e2244182296ad2c5375d0055583dda69e592
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944969"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>如何：檢視、儲存和設定組建記錄檔

在 Visual Studio IDE 中建置專案之後，您可以在 [輸出] 視窗中檢視該組建的資訊。 例如，使用這項資訊，您可以針對建置失敗進行疑難排解。 對於 C++ 專案，您也可以在自動建立和儲存的 *.txt* 檔案中，檢視相同的資訊。 對於受控碼專案，您可以將 [輸出] 視窗的資訊複製並貼至 *.txt* 檔案，然後自行儲存它。 您也可以使用 IDE 來指定您想要檢視每個組建的資訊種類。

如果您使用 MSBuild 建置任何種類的專案，您可以建立 *.txt* 檔案以儲存組建資訊。 如需詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

## <a name="to-view-the-build-log-file-for-a-c-project"></a>檢視 C++ 專案的組建記錄檔

1.  在 **Windows 檔案總管**或**檔案總管**中，開啟下列檔案：*\\...\Visual Studio \<版本\>\Projects\\<專案名稱\>\\<專案名稱\>\Debug\\<專案名稱\>.txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>建立受控碼專案的組建記錄檔

1.  在功能表列上選擇 [建置] > [建置解決方案]。

2.  在 [輸出] 視窗中，反白顯示來自組建的資訊，然後將它複製到剪貼簿。

3.  開啟文字編輯器，例如 [記事本]，將資訊貼到檔案中，然後儲存它。

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>變更組建記錄檔中包含的資訊量

1.  在功能表列上選擇 [工具] > [選項]。

2.  在 [專案和解決方案] 頁面上，選擇 [建置並執行] 頁面。

3.  在 [MSBuild 專案建置輸出詳細資訊層級] 清單中，選擇下列其中一個值，然後選擇 [確定] 按鈕。

    |詳細資訊層級|描述|
    |---------------------|-----------------|
    |**無訊息**|只顯示組建摘要。|
    |**最少**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息。|
    |**正常**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息，還有組建的主要步驟。 您將最常使用此詳細層級。|
    |**詳細**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息，組建的所有步驟，以及分類為正常重要性的訊息。|
    |**診斷**|顯示組建可用的所有資料。 您可以使用此詳細層級以協助偵錯自訂建置指令碼的問題和其他組建問題。|

     如需詳細資訊，請參閱[選項對話方塊、專案和解決方案、建置並執行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)及 <xref:Microsoft.Build.Framework.LoggerVerbosity>。

    > [!IMPORTANT]
    > 您必須重建專案，您的變更才會在 [輸出] 視窗 (所有專案) 和 *<ProjectName>.txt* 檔案 (僅限 C++ 專案) 中生效。

## <a name="see-also"></a>另請參閱

- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
- [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [編譯及建置](../ide/compiling-and-building-in-visual-studio.md)