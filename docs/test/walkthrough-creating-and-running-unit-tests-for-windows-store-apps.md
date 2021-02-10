---
title: 建立並執行 UWP 應用程式的單元測試
description: '瞭解 Visual Studio 通用 Windows 平臺應用程式單元測試的支援。 Visual Studio 提供適用于 c #、Visual Basic 和 c + + 的單元測試範本。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 52b7712c3e2e283dc92da3b920eccdcb0c312cd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948032"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>逐步解說：建立並執行 UWP App 的單元測試

Visual Studio 包含進行通用 Windows 平台 (UWP) 應用程式單元測試的支援。 Visual Studio 提供適用于 c #、Visual Basic 和 c + + 的單元測試專案範本。

> [!TIP]
> 如需開發 UWP 應用程式的詳細資訊，請參閱 [UWP 應用程式入門](/windows/uwp/get-started/)。

下列程式說明針對 UWP 應用程式建立、執行和偵測單元測試的步驟。

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>建立 UWP 應用程式的單元測試專案

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。 在 [開始] 視窗中，選擇 [ **建立新專案**]。

2. 在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 [ **單元測試**]。

   範本清單會篩選這些範本以進行單元測試。

3. 針對 c # 或 Visual Basic 選取 **(通用 Windows) 範本的單元測試應用程式** ，然後選取 **[下一步]**。

   ![在 Visual Studio 中建立新的 UWP 單元測試應用程式](media/vs-2019/new-uwp-unit-test-app.png)

4. （選擇性）變更專案或方案名稱和位置，然後選取 [ **建立**]。

5. （選擇性）變更目標和最低平臺版本，然後選取 **[確定]**。

完成這些步驟之後，就會建立單元測試專案，並在方案總管中顯示。

![方案總管中的 UWP 單元測試專案](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. 從 [ **檔案** ] 功能表選擇 [ **新增專案**]。

   [新增專案] 對話方塊隨即顯示。

2. 在 [範本] 下，選擇您要用來建立單元測試的程式設計語言，然後選擇相關聯的 Windows 通用單元測試程式庫。 例如，依序選擇 [Visual C#]、[Windows 通用] 和 [單元測試程式庫 (通用 Windows)]。

3. (選擇性) 在 [名稱] 文字方塊中，輸入專案要使用的名稱。

4. (選擇性) 在 [位置] 文字方塊中輸入路徑，或是選取 [瀏覽] 按鈕，以修改要建立專案的路徑。

5. (選擇性) 在 [ **方案** ] 名稱文字方塊中，輸入您的方案要使用的名稱。

6. 保留選取 [ **為方案建立目錄** ] 選項，並選擇 [ **確定** ] 按鈕。

   ![量身打造的單元測試程式庫](../test/media/unit_test_win8_1.png)

   **方案總管** 會填入 UWP 單元測試專案，而且程式碼編輯器會顯示標題為 UnitTest1 的預設單元測試。

   ![新量身打造的單元測試專案](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>編輯單元測試專案的 UWP 應用程式資訊清單檔

1. 在 **方案總管** 中，以滑鼠右鍵按一下 *package.appxmanifest* 檔案，然後選擇 [ **開啟**]。

2. 在 [資訊清單設計工具] 中，選擇 [功能] 索引標籤。

3. 在 [ **功能**] 底下的清單中，選取您要讓單元測試及其所測試之程式碼具有的功能。 例如，如果單元測試需要且測試中的程式碼必須有存取網際網路的能力時，則選擇 [ **網際網路** ] 核取方塊。

   > [!NOTE]
   > 您選取的功能應該只包含讓單元測試正常運作的功能。

   ![單元測試資訊清單](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>撰寫 UWP 應用程式的單元測試程式碼

在程式碼編輯器中，編輯單元測試，並加入測試所需的判斷提示和邏輯。

## <a name="run-unit-tests"></a>執行單元測試

若要建立方案，並使用 Test Explorer 來執行單元測試：

1. 在 [ **測試** ] 功能表上，選擇 [ **Windows**]，然後選擇 [ **測試總管**]。

2. 從 [ **組建** ] 功能表中，選擇 [ **建立方案**]。

   您的單元測試現在會顯示在 Test Explorer 中。

   > [!NOTE]
   > 您必須建置方案以更新 [測試總管] 中的單元測試清單。

3. 在 [ **測試瀏覽器**] 中，選擇您所建立的單元測試。

4. 選擇 [ **全部執行**]。

   ![單元測試總管 &#45; 執行單元測試](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > 您可以選取 [Test Explorer] 中所列的一或多個單元測試，然後以滑鼠右鍵按一下並選擇 [ **執行選取的測試**]。
   >
   > 此外，您可以選擇 [ **偵錯選取的測試**]、[ **開啟測試**]，並使用 [ **屬性** ] 選項。
   >
   > ![單元測試瀏覽器 &#45; 單元測試內容功能表](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   單元測試隨即執行。 完成時，Test Explorer 會顯示測試狀態和經過時間，並提供來源的連結。

   ![單元測試總管 &#45; 測試完成](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 測試 UWP 應用程式](../test/unit-test-your-code.md)
- [建置並測試 UWP 應用程式](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
