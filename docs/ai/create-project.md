---
title: 從範本建立 AI 專案
description: 瞭解如何使用 Visual Studio Tools for AI 從各種範本建立 AI 專案。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: dbef3f71678f899a41e7b4db7e1d8123952d4f75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841480"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>在 Visual Studio 中從範本建立 AI 專案

[安裝 Visual Studio Tools for AI](installation.md) 後，您就可以使用各種範本輕鬆地建立新的 AI 專案。

1. 啟動 Visual Studio。

2. 選取 [檔案] > [新增] > [專案] (Ctrl+Shift+N)。 在 [新增專案] 對話方塊中，搜尋 "**AI Tools**"，然後選取您想要的範本。 請注意，選取範本時會顯示範本所提供項目的簡短描述 

    ![含 Python 範本的 VS2017 [新增專案] 對話方塊](media/create-project/new-ai-project.png)

3. 在本快速入門中，選取 [TensorFlow 應用程式] 範本，並提供專案的名稱 (例如 "MNIST") 和位置，然後選取 [確定]。

4. Visual Studio 會建立專案檔 (磁碟上的 `.pyproj` 檔案) 以及範本所述的任何其他檔案。 使用 [TensorFlow 應用程式] 範本，專案會包含一個名稱與您專案相同的檔案。 根據預設，會在 Visual Studio 編輯器中開啟檔案。

    ![使用 Python 應用程式範本時所產生的專案](media/create-project/new-tensorflowapp.png)

5. 請注意，此程式碼已經匯入多個程式庫，包括 TensorFlow、numpy、sys 及 os。 此外還可讓您的應用程式啟動就緒，並附帶一些輸入引數，以便輕鬆切換輸入定型資料、輸出模型及記錄檔的位置。 當您將作業提交到多個計算內容 (亦即本機開發人員方塊上與 Azure 檔案共用不同的目錄) 時，這些參數會很實用。

6. 您的專案也有一些已建立的屬性，會自動將命令列引數傳遞到這些輸入參數，讓應用程式的偵錯程序變得更簡單。 **以滑鼠右鍵按一下** 您的專案，然後選取 [屬性]

    ![Visual Studio 方案總管的螢幕擷取畫面，其中顯示已選取屬性的 TensorFlowApplication1 內容功能表。](media/create-project/project-properties.png)

7. 按一下[偵錯] 索引標籤以查看自動新增的指令碼引數。 您可以視需求變更輸入資料的位置，以及輸出的儲存位置。

    ![顯示專案腳本引數的 TensorFlowApplication1 [屬性] 設定中，[偵錯工具] 索引標籤的螢幕擷取畫面。](media/create-project//project-properties_1.png)

8. 按 Ctrl+F5，或是選取功能表上的 [偵錯] > [啟動但不偵錯]，以執行程式。 結果會顯示在主控台視窗中。
