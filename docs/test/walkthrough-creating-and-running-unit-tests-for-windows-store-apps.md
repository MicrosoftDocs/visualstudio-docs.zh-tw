---
title: 建立並執行 UWP 應用程式的單元測試
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 1284dc529e4f150b282dcab2d919e027c9b606c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976431"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>逐步解說：建立並執行 UWP App 的單元測試

Visual Studio 包含進行通用 Windows 平台 (UWP) 應用程式單元測試的支援。 它包含 Visual C#、Visual Basic 和 Visual C++ 的單元測試專案範本。

> [!TIP]
> 如需開發 UWP 應用程式的詳細資訊，請參閱 [UWP 應用程式入門](/windows/uwp/get-started/)。

下列程序說明用來建立、執行和偵錯 UWP 應用程式的單元測試之步驟。

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>建立 UWP 應用程式的單元測試專案

1. 從 [ **檔案** ] 功能表選擇 [ **新增專案**]。

     [新增專案] 對話方塊隨即顯示。

2. 在 [範本] 下，選擇您要用來建立單元測試的程式設計語言，然後選擇相關聯的 Windows 通用單元測試程式庫。 例如，依序選擇 [Visual C#]、[Windows 通用] 和 [單元測試程式庫 (通用 Windows)]。

3. (選擇性) 在 [名稱] 文字方塊中，輸入專案要使用的名稱。

4. (選擇性) 在 [位置] 文字方塊中輸入路徑，或是選取 [瀏覽] 按鈕，以修改要建立專案的路徑。

5. (選擇性) 在 [ **方案** ] 名稱文字方塊中，輸入您的方案要使用的名稱。

6. 保留選取 [ **為方案建立目錄** ] 選項，並選擇 [ **確定** ] 按鈕。

     ![量身打造的單元測試程式庫](../test/media/unit_test_win8_1.png)

     您的 UWP 單元測試專案隨即填入 [方案總管] 中，並且程式碼編輯器中會顯示預設的單元測試標題 - UnitTest1。

     ![新量身打造的單元測試專案](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>編輯單元測試專案的 UWP 應用程式資訊清單檔

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *Package.appxmanifest* 檔案並選擇 [開啟]。

     [資訊清單設計工具] 隨即顯示，可供編輯。

2. 在 [資訊清單設計工具] 中，選擇 [功能] 索引標籤。

3. 在 [ **功能**] 底下的清單中，選取您要讓單元測試及其所測試之程式碼具有的功能。 例如，如果單元測試需要且測試中的程式碼必須有存取網際網路的能力時，則選擇 [ **網際網路** ] 核取方塊。

    > [!NOTE]
    > 您選取的功能應該只包含讓單元測試正常運作的功能。

     ![單元測試資訊清單](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>撰寫 UWP 應用程式的單元測試程式碼

在 [程式碼編輯器] 中，編輯單元測試，並加入測試所需的判斷提示和邏輯。

## <a name="run-unit-tests"></a>執行單元測試

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>若要使用測試總管建置方案與執行單元測試

1. 在 [ **測試** ] 功能表上，選擇 [ **Windows**]，然後選擇 [ **測試總管**]。

     [測試總管] 隨即顯示，但沒有列出您的測試。

2. 從 [ **建置** ] 功能表中，選擇 [ **建置方案**]。

     現在列出了您的單元測試。

    > [!NOTE]
    > 您必須建置方案以更新 [測試總管] 中的單元測試清單。

3. 在 [測試總管] 中，選擇您建立的單元測試。

    > [!TIP]
    > [測試總管] 會在 [ **來源:**] 旁邊提供原始程式碼的連結。

4. 選擇 [ **全部執行**]。

     ![單元測試總管 &#45; 執行單元測試](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > 您可以選取 [測試總管] 中列出的一個或多個單元測試，然後以滑鼠右鍵按一下並選擇 [ **執行選取的測試**]。
    >
    > 此外，您可以選擇 [ **偵錯選取的測試**]、[ **開啟測試**]，並使用 [ **屬性** ] 選項。
    >
    > ![[單元測試總管] &#45; 單元測試操作功能表](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

    單元測試隨即執行。 完成時，[測試總管] 會顯示測試狀態、已耗用時間並提供來源連結。

    ![單元測試總管 &#45; 測試完成](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 測試 UWP 應用程式](../test/unit-test-your-code.md)
- [建置並測試 UWP 應用程式](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)