---
title: 如何：檢視、儲存和設定組建記錄檔 | Microsoft Docs
description: 瞭解您可以如何查看、儲存和設定組建記錄檔。 這些檔案會提供實用的工作資訊，例如針對組建失敗進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02d26416357ec13b61232f2adb0bc3e5e3c67818
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970206"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>如何：檢視、儲存和設定組建記錄檔

在 Visual Studio IDE 中建置專案之後，您可以在 [輸出] 視窗中檢視該組建的資訊。 例如，使用這項資訊，您可以針對建置失敗進行疑難排解。

- 若是 c + + 專案，您也可以在建立專案時所建立和儲存的記錄檔中，查看相同的資訊。 

- 針對 managed 程式碼專案，您可以按一下 [組建輸出] 視窗，然後按 **Ctrl** + **S**。 Visual Studio 會提示您輸入一個位置，將資訊從 **輸出** 視窗儲存到記錄檔中。

您也可以使用 IDE 來指定您想要檢視每個組建的資訊種類。

如果您使用 MSBuild 建立任何類型的專案，您可以建立記錄檔來儲存組建的相關資訊。 如需詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

## <a name="to-view-the-build-log-file-for-a-c-project"></a>檢視 C++ 專案的組建記錄檔

1. 在 **Windows 檔案總管** 或 **檔案總管** 中，開啟下列檔 (相對於專案根資料夾) ： *Release* \\ <ProjectName> \> 。Log * 或 *Debug \\<專案名稱 \> .log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>建立受控碼專案的組建記錄檔

1. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

2. 在 [輸出] 視窗中，按一下文字中的某處。

3. 按下 **Ctrl** + **S**。

   Visual Studio 會提示您輸入要儲存建置輸出的位置。

您也可以透過直接從命令列執行 MSBuild (使用 `-fileLogger` (`-fl`) 命令列選項) 來產生記錄。 請參閱[使用 MSBuild 取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>變更組建記錄檔中包含的資訊量

1. 在功能表列上，選擇 [**工具**  >  **選項**]。

2. 在 [專案和解決方案] 頁面上，選擇 [建置並執行] 頁面。

3. 在 [MSBuild 專案建置輸出詳細資訊層級] 清單中，選擇下列其中一個值，然後選擇 [確定] 按鈕。

    |詳細資訊層級|描述|
    | - |-----------------|
    |**Quiet**|只顯示組建摘要。|
    |**最低限度**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息。|
    |**Normal**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息，還有組建的主要步驟。 您將最常使用此詳細層級。|
    |**詳細**|顯示組建的摘要，及已分類為高重要性的錯誤、警告和訊息，組建的所有步驟，以及分類為正常重要性的訊息。|
    |**Diagnostic**|顯示組建可用的所有資料。 您可以使用此詳細層級以協助偵錯自訂建置指令碼的問題和其他組建問題。|

     如需詳細資訊，請參閱[選項對話方塊、專案和解決方案、建置並執行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)及 <xref:Microsoft.Build.Framework.LoggerVerbosity>。

    > [!IMPORTANT]
    > 您必須重建專案，您的變更才會在 [輸出] 視窗 (所有專案) 和 *\<ProjectName>.txt* 檔案 (僅限 C++ 專案) 中生效。

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>使用二進位記錄檔來輕鬆瀏覽大型記錄檔

二進位記錄檔是適用於 .NET 專案的選擇性功能，它可讓您擁有更豐富的記錄檔瀏覽體驗，以便您可以輕鬆地在大型記錄中尋找資訊。 若要使用二進位記錄檔，請安裝 [Project System Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)。 如需詳細資訊，請參閱 [https://msbuildlog.com](https://msbuildlog.com) 和[二進位記錄](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)檔

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
