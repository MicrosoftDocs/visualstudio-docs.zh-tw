---
title: 從現有程式碼建立 AI 專案
description: 瞭解如何使用 Visual Studio Tools for AI 將現有的 Python 程式碼帶入 Visual Studio 專案。
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 7746d8dd39bb4400a7779ad43e489cf6e7475fb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841623"
---
# <a name="create-an-ai-project-from-existing-code"></a>從現有程式碼建立 AI 專案

在[安裝適用於 AI 的 Visual Studio Tools](installation.md) 之後，您就可以輕鬆的將現有的 Python 程式碼帶入 Visual Studio 專案中。

> [!Important]
> 此處所述的程序不會移動或複製原始程式檔。 如果您想要使用複本，請先複製資料夾。

1. 啟動 Visual Studio，然後選取 [檔案] > [新增] > [專案]。

2. 在 [新增專案] 對話方塊中，搜尋「**AI 工具**」，並選取 [從現有 Python 程式碼] 範本，再提供專案名稱和位置，然後選取 [確定]。

   ![從現有程式碼新增專案 - 步驟 1](media/create-project-existing/new-ai-project.png)

3. 在出現的精靈中，設定您現有程式碼的路徑、設定檔案類型的篩選條件，並指定您專案所需的任何搜尋路徑，然後選取 [確定]。 如果您不知道搜尋路徑為何，請將該欄位留白。

   ![從現有程式碼新增專案 - 步驟 2](media/create-project-existing/azurebatch-newproject.png)

   若您現有的程式碼是 Azure Machine Learning 專案的一部分，請勾選 [Is Azure Machine Learning folder] (這是 Azure Machine Learning 資料夾) 以確保重要的 Azure Machine Learning 設定詳細資料 (例如要使用的實驗帳戶、工作區與計算內容等) 可成功轉換。

4. 若要設定啟動檔案，請在 [方案總管] 中找到檔案，並按一下滑鼠右鍵，然後選取 [設定為啟動檔案]。

5. 按下 **Ctrl** + **F5** 或選取 **Debug > 啟動但不進行調試** 程式來執行程式。

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>另請參閱

- [手動識別現有的 Python 環境](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
