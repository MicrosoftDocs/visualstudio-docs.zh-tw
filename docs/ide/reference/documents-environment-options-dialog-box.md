---
title: 選項對話方塊、環境、文件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ceccf3c051e3c85fa4b8e64ecbc33c388e9a884f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178175"
---
# <a name="documents-environment-options-dialog-box"></a>選項對話方塊、環境、文件
使用 [選項] 對話方塊的這個頁面，即可控制整合式開發環境 (IDE) 中的文件顯示，以及管理文件和檔案的外部變更。 按一下 [工具] 功能表上的 [選項]，然後選取 [環境] 節點中的 [文件]，即可存取此對話方塊。 如果 [文件] 未出現在清單中，請在 [選項] 對話方塊中選取 [顯示所有設定]。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。


 **重複使用目前的文件視窗 (如果已儲存)**：選取時，如果目前的文件已儲存，則會將它關閉然後在同一個視窗中開啟新文件。 如果尚未儲存您目前的文件，則仍然會保持開啟，並在個別視窗中開啟新文件。 清除此選項時，一律會在個別視窗中開啟新文件。

 如果您不常執行多文件剪下和貼上作業，而且想要將工作空間中開啟的文件和視窗數目降至最低，請嘗試使用此選項。

 **當檔案在環境以外變更時偵測**：選取此選項時，若開啟中的檔案已由 IDE 外的編輯器變更，便會立刻出現訊息通知您。 此訊息可讓您從儲存體重新載入檔案。

 **自動載入變更 (如果已儲存)**：如果您已選取 [當檔案在環境以外變更時偵測]，且 IDE 中已開啟的檔案在 IDE 外部變更，則預設會產生警告訊息。 如果啟用此選項，則不會顯示警告，並且會在 IDE 中重新載入文件以反映外部變更。

 **允許編輯唯讀檔案，當嘗試儲存時警告**：啟用此選項時，您可以開啟和編輯唯讀檔案。 當您完成時，如果想要儲存變更記錄，則必須使用 [另存新檔] 命令將檔案儲存為新名稱。

 **使用目前現用文件的目錄開啟檔案**：選取時，此選項會指定 [開啟檔案] 對話方塊顯示使用中文件的目錄。 清除此選項時，[開啟檔案] 對話方塊會顯示上次用來開啟檔案的目錄。

 **載入時檢查行尾結束符號是否一致**：選取此選項，可讓編輯器掃描檔案中的行尾結束符號，並在偵測到行尾結束符號格式設定不一致時，顯示訊息方塊。

 **當全域復原要修改已編輯的檔案時，顯示警告**：選取此選項，當 [全域復原] 命令復原重構作業之後所變更檔案中的重構變更時，顯示訊息方塊。 將檔案還原為其重構前狀態，可能會捨棄後續在檔案中進行的變更。

 **在方案總管中顯示其他檔案**：選取此選項可在 [方案總管] 中顯示 [其他檔案] 節點。 其他檔案是與專案或方案無關，但為了方便您使用而出現在方案總管中。

> [!NOTE]
> 選取此選項，可針對使用中 Web 應用程式未包含的 Web 文件啟用 [檔案] 功能表上的 [在瀏覽器中檢視] 命令。

 **\<** *n* **> 個項目儲存在其他檔案專案中**：指定在 [方案總管] 中 [其他檔案] 資料夾中保存的檔案數目。 即使不再於編輯器中開啟這些檔案，還是會列出這些檔案。 您可以指定從 0 到 256 的任何整數。 預設數字是 0。

 例如，如果您將此選項設定為 5，並且開啟 10 個其他檔案，則關閉全部 10 個檔案時，前 5 個檔案仍然會顯示在 [其他檔案] 資料夾中。

 **無法以字碼頁儲存資料時，將文件儲存為 Unicode**：選取此選項，針對包含的資訊與所選取字碼頁不相容的檔案，預設將檔案儲存為 Unicode。

## <a name="see-also"></a>另請參閱

- [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)
- [其他檔案](../../ide/reference/miscellaneous-files.md)
- [尋找和取代文字](../../ide/finding-and-replacing-text.md)