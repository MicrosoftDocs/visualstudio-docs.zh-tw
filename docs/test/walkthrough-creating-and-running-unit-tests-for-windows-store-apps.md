---
title: 建立並執行 UWP 應用程式的單元測試
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568876"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>逐步解說：建立並執行 UWP 應用程式的單元測試

Visual Studio 包含進行通用 Windows 平台 (UWP) 應用程式單元測試的支援。 Visual Studio 為 C#、視覺化基本版和C++提供單元測試專案範本。

> [!TIP]
> 如需開發 UWP 應用程式的詳細資訊，請參閱 [UWP 應用程式入門](/windows/uwp/get-started/)。

以下過程描述了為 UWP 應用創建、運行和調試單元測試的步驟。

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>建立 UWP 應用程式的單元測試專案

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。 在啟動視窗中，選擇 **"創建新專案**"。

2. 在 **"創建新專案**"頁的搜索框中，輸入**單元測試**。

   範本清單篩選到用於單元測試的範本。

3. 為 C# 或視覺化基本選擇 **"單元測試應用（通用 Windows）"** 範本，然後選擇 **"下一步**"。

   ![在視覺化工作室創建新的 UWP 單元測試應用](media/vs-2019/new-uwp-unit-test-app.png)

4. 可以選擇更改專案或解決方案名稱和位置，然後選擇 **"創建**"。

5. 可以選擇更改目標和最小平臺版本，然後選擇 **"確定**"。

完成這些步驟後，將創建單元測試專案，並在解決方案資源管理器中顯示。

![解決方案資源管理器中的 UWP 單元測試專案](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. 從 [ **檔案** ] 功能表選擇 [ **新增專案**]。

   [新增專案]**** 對話方塊隨即顯示。

2. 在 [範本] 下，選擇您要用來建立單元測試的程式設計語言，然後選擇相關聯的 Windows 通用單元測試程式庫。 例如，依序選擇 [Visual C#]****、[Windows 通用]**** 和 [單元測試程式庫 (通用 Windows)]****。

3. (選擇性) 在 [名稱]**** 文字方塊中，輸入專案要使用的名稱。

4. (選擇性) 在 [位置]**** 文字方塊中輸入路徑，或是選取 [瀏覽]**** 按鈕，以修改要建立專案的路徑。

5. (選擇性) 在 [ **方案** ] 名稱文字方塊中，輸入您的方案要使用的名稱。

6. 保留選取 [ **為方案建立目錄** ] 選項，並選擇 [ **確定** ] 按鈕。

   ![量身打造的單元測試程式庫](../test/media/unit_test_win8_1.png)

   **解決方案資源管理器**填充了 UWP 單元測試專案，代碼編輯器顯示名為 UnitTest1 的預設單元測試。

   ![新量身打造的單元測試專案](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>編輯單元測試專案的 UWP 應用程式資訊清單檔

1. 在**解決方案資源管理器**中，按右鍵*包.appxmanifest 檔*，然後選擇 **"打開**"。

2. 在 [資訊清單設計工具]**** 中，選擇 [功能]**** 索引標籤。

3. 在 [ **功能**] 底下的清單中，選取您要讓單元測試及其所測試之程式碼具有的功能。 例如，如果單元測試需要且測試中的程式碼必須有存取網際網路的能力時，則選擇 [ **網際網路** ] 核取方塊。

   > [!NOTE]
   > 您選取的功能應該只包含讓單元測試正常運作的功能。

   ![單元測試資訊清單](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>撰寫 UWP 應用程式的單元測試程式碼

在代碼編輯器中，編輯單元測試，並添加測試所需的斷言和邏輯。

## <a name="run-unit-tests"></a>執行單元測試

要生成解決方案並使用測試資源管理器運行單元測試，請使用：

1. 在 [ **測試** ] 功能表上，選擇 [ **Windows**]，然後選擇 [ **測試總管**]。

2. 在 **"生成"** 功能表中，選擇 **"生成解決方案**"。

   您的單元測試現在顯示在測試資源管理器中。

   > [!NOTE]
   > 您必須建置方案以更新 [測試總管] 中的單元測試清單。

3. 在**測試資源管理器中**，選擇您創建的單元測試。

4. 選擇 [ **全部執行**]。

   ![單元測試總管 &#45; 執行單元測試](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > 您可以選擇測試資源管理器中列出的一個或多個單元測試，然後按右鍵並選擇 **"運行所選測試**"。
   >
   > 此外，您可以選擇 [ **偵錯選取的測試**]、[ **開啟測試**]，並使用 [ **屬性** ] 選項。
   >
   > ![單元測試資源管理器&#45;單元測試內容功能表](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   單元測試隨即執行。 完成後，測試資源管理器將顯示測試狀態和執行時間，並提供指向源的連結。

   ![單元測試總管 &#45; 測試完成](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 測試 UWP 應用程式](../test/unit-test-your-code.md)
- [建置並測試 UWP 應用程式](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
