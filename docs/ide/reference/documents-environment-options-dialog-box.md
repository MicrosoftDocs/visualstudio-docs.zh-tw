---
title: 選項對話方塊、環境、文件
description: 瞭解如何使用 [檔] 區段中的 [環境] 頁面，控制 IDE 中的檔顯示，以及管理檔和檔案的外部變更。
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9ed6833bd60854cf2e3bcfbab76d57c7010f7863
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882130"
---
# <a name="options-dialog-box-environment--documents"></a>選項對話方塊：環境 \> 檔

使用 [選項] 對話方塊的這個頁面，即可控制整合式開發環境 (IDE) 中的文件顯示，以及管理文件和檔案的外部變更。 按一下 [工具] 功能表上的 [選項]，然後選取 [環境] > [文件]，即可存取此對話方塊。

**當檔案在環境以外變更時偵測**

選取此選項時，會有一則訊息立即通知您：編輯器已在 IDE 外部變更已開啟的檔案。 此訊息可讓您從儲存體重新載入檔案。

**除非檔案中有未儲存的變更，否則重新載入修改過的檔案**

如果您已選取 [當檔案在環境以外變更時偵測]，並且 IDE 中的已開啟檔案在 IDE 外部變更，則預設會產生警告訊息。 如果啟用此選項，則不會顯示警告，並且會在 IDE 中重新載入文件以反映外部變更。

**允許編輯唯讀檔案，當嘗試儲存時警告**

啟用此選項時，您可以開啟和編輯唯讀檔。 當您完成時，如果想要儲存變更記錄，則必須使用 [另存新檔] 命令將檔案儲存為新名稱。

**使用目前現用文件的目錄開啟檔案**

選取時，此選項指定 [開啟檔案] 對話方塊會顯示使用中文件的目錄。 清除此選項時，[開啟檔案] 對話方塊會顯示上次用來開啟檔案的目錄。

**載入時檢查行尾結束符號是否一致**

選取此選項，可讓編輯器掃描檔案中的行尾結束符號，並在格式化行尾結束符號時偵測到不一致時顯示訊息方塊。

**當全域復原要修改已編輯的檔案時，顯示警告**

選取此選項，可在 [全域復原] 命令復原重構在檔案中進行的變更而這些變更也會在重構作業之後變更時顯示訊息方塊。 將檔案還原為其重構前狀態，可能會捨棄後續在檔案中進行的變更。

**在方案總管中顯示其他檔案**

選取此選項，可在方案總管中顯示 [其他檔案] 節點。 其他檔案是與專案或方案無關，但為了方便您使用而出現在方案總管中。

> [!NOTE]
> 選取此選項，即可在 [檔案] 功能表上的 [檔案] 功能表上，針對未包含在使用中 web 應用程式的 web **檔** 啟用 [**流覽**] 命令

**儲存在其他檔案專案中的項目**

指定在 [方案總管] 的 [其他檔案] 資料夾中保存的檔案數目。 即使不再於編輯器中開啟這些檔案，還是會列出這些檔案。 您可以指定從 0 到 256 的任何整數。 預設數字是 0。

例如，如果您將此選項設定為 5，並且開啟 10 個其他檔案，則關閉全部 10 個檔案時，前 5 個檔案仍然會顯示在 [其他檔案] 資料夾中。

**無法以字碼頁儲存資料時，將文件儲存為 Unicode**

選取此選項，預設會將包含所選取字碼頁不相容資訊的檔案儲存為 Unicode。

## <a name="see-also"></a>另請參閱

- [其他檔案](../../ide/reference/miscellaneous-files.md)
- [尋找和取代文字](../../ide/finding-and-replacing-text.md)
