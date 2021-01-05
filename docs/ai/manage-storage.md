---
title: 瀏覽儲存體以上傳資料
description: 瞭解如何流覽遠端電腦或 Azure 檔案共用上的所有存放裝置，以啟用上傳資料或下載模型與記錄。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: b145c4acf4047356b8996d09d746679900314f1b
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726562"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>瀏覽儲存體以上傳資料或下載模型和記錄檔

您可以瀏覽位於遠端電腦或 Azure 檔案共用上的所有儲存體，來啟用上傳資料或下載模型及記錄檔。 若您想要存取特定作業的記錄檔和作業輸出，您也可以在作業瀏覽器中進行。

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>若要存取位於遠端電腦或檔案共用的所有資料

1. 開啟 [伺服器總管]。
2. 展開遠端電腦或批次 AI 計算內容。
3. 以滑鼠右鍵按一下 [儲存體]，然後按一下 [瀏覽]。

    ![展開 [遠端電腦] 資料夾之伺服器總管的螢幕擷取畫面。 資料夾樹狀目錄中會反白顯示儲存體，並在內容功能表上選取 [流覽]。](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>若要存取位於遠端電腦或檔案共用上的特定作業資料

1. 請開啟[作業歷程記錄](job-details.md)
2. 選取工作。
3. 按一下 [工作資料夾] 或按一下 [StdOut / Stderr] 以快速存取這些重要記錄檔。

    ![伺服器總管中 [作業瀏覽器] 視窗的螢幕擷取畫面。 已選取 [train_mnist] 作業，並在 [工作詳細資料] 底下選取 [工作資料夾] 連結。](media/manage-storage/job-workingfolder.png)
