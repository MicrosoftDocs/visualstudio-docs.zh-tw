---
title: 不使用專案或方案來開發程式碼
description: 瞭解如何直接在 Visual Studio 中開發程式碼，而不需要專案或解決方案。
ms.custom: SEO-VS-2020
ms.date: 06/22/2020
ms.topic: how-to
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcff44b64045e85a06fdc7a8f15f8780c8453713
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894747"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>在 Visual Studio 中不使用專案或方案來開發程式碼

您可以在 Visual Studio 中從幾乎任何類型的目錄型專案開啟程式碼，而不需使用解決方案或專案檔。 例如，這表示您可以在 GitHub 上複製存放庫，然後直接在 Visual Studio 中開啟它並開始開發，而不需建立方案或專案。 若有需要，您可以透過簡單的 JSON 檔案指定自訂建置工作並啟動參數。

當您在 Visual Studio 中開啟程式碼檔案之後，方案總管便會顯示資料夾中的所有檔案。 您可以按一下任何檔案以開始編輯它。 Visual Studio 會在背景開始編制檔案的索引，以啟用 IntelliSense、瀏覽及重構功能。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 程式碼的語法會以色彩標示，並且在許多情況下包含基本的 IntelliSense 陳述式完成。

## <a name="open-any-code"></a>開啟任何程式碼

您可以透過下列方式在 Visual Studio 中開啟程式碼：

- 在 [Visual Studio] 功能表列上 **，選擇 [** 檔案  >  **開啟**  >  **資料夾**]，然後流覽至程式碼位置。

- 在包含程式碼之資料夾 (按一下滑鼠右鍵) 的操作功能表上，選擇 [在 Visual Studio 中開啟] 命令。

::: moniker range="vs-2017"
- 在 Visual Studio [起始頁] 上，選擇 [開啟資料夾] 連結。

    > [!IMPORTANT]
    > 並非所有程式碼都可以使用 Visual Studio **起始頁** 的 [**開啟資料夾**] 連結來開啟。 例如，如果您的程式碼檔案儲存為方案的一部分 &mdash; ，則在 .sln 檔案中， &mdash; 您必須使用此處所列的其中一個其他選項來開啟您的程式碼。

::: moniker-end

::: moniker range=">=vs-2019"
- 在 [開始] 視窗上，選擇 [開啟資料夾] 連結。

    > [!IMPORTANT]
    > 並非所有程式碼都可以使用 Visual Studio 開始視窗中的 [ **開啟資料夾** ] 連結來開啟。 例如，如果您的程式碼檔案儲存為方案的一部分 &mdash; ，則在 .sln 檔案中， &mdash; 您必須使用此處所列的其中一個其他選項來開啟您的程式碼。

::: moniker-end

- 如果您是鍵盤使用者，請按 +  + Visual Studio 中的 Ctrl Shift **Alt** + **O** 。

- 從複製的 GitHub 存放庫開啟程式碼。

### <a name="to-open-code-from-a-cloned-github-repo"></a>從複製的 GitHub 儲存機制開啟程式碼

下列範例說明如何複製 GitHub 儲存機制，然後在 Visual Studio 中開啟其程式碼。 若要依照此程序，您必須擁有 GitHub 帳戶並在您的系統上安裝 Git for Windows。 如需詳細資訊，請參閱[註冊新的 GitHub 帳戶 (英文)](https://help.github.com/articles/signing-up-for-a-new-github-account/) 和 [Git for Windows (英文)](https://git-for-windows.github.io/)。

1. 移至您想要複製到 GitHub 的存放庫。

1. 選擇 [Clone or Download] (複製或下載) 按鈕，然後選擇下拉式清單中的 [複製到剪貼簿] 按鈕，以複製 GitHub 存放庫的安全 URL。

   ![GitHub 複製按鈕](./media/VSIDE_Code_Clone.png)

1. 在 Visual Studio 中，選擇 [Team Explorer] 索引標籤以開啟 [Team Explorer]。 如果您沒有看到此索引標籤，請從 [ **View**  >  **Team Explorer**] 開啟它。

1. 在 [Team Explorer] 中的 [本機 Git 儲存機制] 區段底下，選擇 [複製] 命令，然後將 GitHub 頁面的 URL 貼到文字方塊中。

   ![複製專案](./media/VSIDE_Code_Clone2.png)

1. 選擇 [複製] 按鈕，以將專案的檔案複製到本機 Git 儲存機制。 視儲存機制的大小而定，此程序可能會花費數分鐘的時間。

1. 將存放庫複製到您的系統之後，在 **Team Explorer** 中，選擇 [ **開啟** ] 命令， (以滑鼠右鍵按一下新複製的存放庫) 功能表。

   ![複製的存放庫](./media/VSIDE_Code_Clone3.png)

1. 選擇 [顯示資料夾檢視] 命令，以在方案總管中檢視檔案。

   ![顯示資料夾檢視](./media/VSIDE_Code_Clone3_show.png)

   您現在可以瀏覽所複製存放庫中的資料夾和檔案，並在 Visual Studio 程式碼編輯器中檢視及搜尋程式碼，其中會包含語法色彩標示及其他功能。

## <a name="run-and-debug-your-code"></a>執行程式碼並對它進行偵錯

您可以在不使用專案或方案的情況下，於 Visual Studio 中對程式碼進行偵錯！ 若要針對某些語言進行偵錯，您可能需要在程式碼基底中指定有效的 *啟動檔案*，例如指令碼、可執行檔或專案。 工具列上 [啟動] 按鈕旁邊的下拉式清單除了會列出 Visual Studio 所偵測到的所有啟動項目之外，也會列出您明確指定的項目。 當您對程式碼進行偵錯時，Visual Studio 會先執行此程式碼。

設定程式碼以在 Visual Studio 中執行的方式，會依程式碼類型及使用的建置工具而異。

### <a name="codebases-that-use-msbuild"></a>使用 MSBuild 的程式碼基底

以 MSBuild 為基礎的程式碼基底，在 [啟動] 按鈕的下拉式清單中可能會出現多個組建組態。 選取您想要作為啟動項目使用的檔案，然後選擇 [啟動] 按鈕以開始進行偵錯。

> [!NOTE]
> 針對 C# 和 Visual Basic 程式碼基底，您必須安裝 **.NET 桌面開發** 工作負載。 針對 C++ 程式碼基底，您必須安裝 **使用 C++ 的桌面開發** 工作負載。

### <a name="codebases-that-use-custom-build-tools"></a>使用自訂建置工具的程式碼基底

若您的程式碼基底使用自訂建置工具，您必須使用定義於 *.json* 檔案中的 *建置工作* 來告訴 Visual Studio 建置您程式碼的方式。 如需詳細資訊，請參閱[自訂建置與偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)。

### <a name="codebases-that-contain-python-or-javascript-code"></a>包含 Python 或 JavaScript 程式碼的程式碼基底

若您的程式碼基底包含 Python 或 JavaScript 程式碼，您不需要設定任何 *.json* 檔案，但必須安裝相對應的工作負載。 您也必須設定啟動指令碼：

1. 選擇 [工具] > [取得工具和功能] 或關閉 Visual Studio 並執行 Visual Studio 安裝程式，來安裝 [Node.js 開發](https://visualstudio.microsoft.com/vs/node-js/)工作負載或 [Python 開發](https://visualstudio.microsoft.com/vs/python/)工作負載。

   ![Node.js 和 Python 開發工作負載](media/python_nodejs_workloads.png)

1. 在 [方案總管] 中，在 JavaScript 或 Python 檔案的右鍵功能表或操作功能表上，選擇 [設定為啟動項目] 命令。

1. 選擇 [啟動] 按鈕以開始進行偵錯。

### <a name="codebases-that-contain-c-code"></a>包含 C++ 程式碼的程式碼基底

如需在 Visual Studio 中不搭配方案或專案開啟 C++ 程式碼的相關資訊，請參閱[適用於 C++ 的「開啟資料夾」專案](/cpp/build/open-folder-projects-cpp)。

### <a name="codebases-that-contain-a-visual-studio-project"></a>包含 Visual Studio 專案的程式碼基底

如果您的程式碼資料夾包含 Visual Studio 專案，您可以將該專案指定為啟動項目。

![將專案設定為啟動項目](media/customize-set-project-as-startup-item.png)

[啟動] 按鈕的文字會變更，以反映出該專案已成為啟動項目。

![[啟動] 按鈕上的專案](media/customize-start-button-project.png)

## <a name="see-also"></a>另請參閱

- [自訂建置與偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++ 的開啟資料夾專案](/cpp/build/open-folder-projects-cpp)
- [C++ 中的 CMake 專案](/cpp/build/cmake-projects-in-visual-studio)
- [在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)
