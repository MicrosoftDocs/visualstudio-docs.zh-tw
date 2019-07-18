---
title: 開始使用 C++
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.topic: tutorial
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: a132787a5af0aca9b42775931b343b89710ce91b
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043391"
---
# <a name="get-started-with-c-in-visual-studio"></a>Visual Studio 中的 C++ 使用者入門

完成這個快速入門，以熟悉許多可在 C++ 中使用 Visual Studio 開發應用程式時使用的工具和對話方塊。 建立 "Hello, World" 型主控台應用程式，同時深入了解如何使用整合式開發環境 (IDE)。

## <a name="prerequisites"></a>必要條件

您不需要熟悉 C++ 即可完成此快速入門，但應該熟悉一些一般程式設計和偵錯概念。 Visual Studio 文件不會教導您如何在 C++ 中進行程式設計。 不錯的 C++ 學習資源指南是 ISO C++ 網站上的[使用者入門](https://isocpp.org/get-started)頁面。

::: moniker range="vs-2017"

若要跟著做，您需要一份 Visual Studio 2017 複本，其中已安裝**使用 C++ 的桌面開發**工作負載。 如需安裝的快速指南，請參閱[在 Visual Studio 中安裝 C++ 支援](/cpp/build/vscpp-step-0-installation)。

::: moniker-end

::: moniker range=">=vs-2019"

若要跟著做，您需要一份 Visual Studio 2019 複本，其中已安裝**使用 C++ 的桌面開發**工作負載。 如需安裝的快速指南，請參閱[在 Visual Studio 中安裝 C++ 支援](/cpp/build/vscpp-step-0-installation)。

::: moniker-end

## <a name="create-a-console-app"></a>建立主控台應用程式

如果尚未執行，請開啟 Visual Studio。

::: moniker range="vs-2017"

![已套用 Visual C&#43;&#43; 設定的 IDE](../ide/media/get-started-cpp-ide-layout.png)

開啟 Visual Studio 之後，您會看到 IDE 的三個基本部分：工具視窗、功能表和工具列，以及主視窗空間。 工具視窗停駐在應用程式視窗的左側和右側。 [快速啟動]  方塊、功能表列和標準工具列位於頂端。 視窗中央包含 [起始頁]  。 當您開啟方案或專案時，編輯器和設計工具就會出現在此空間中。 開發應用程式時，您大部分的時間都花在此中央區域。

::: moniker-end

::: moniker range=">=vs-2019"

開啟 Visual Studio 後，會先出現 [開始] 視窗。 選取 [不使用程式碼繼續]  以開啟開發環境。

您會看到 IDE 的三個基本部分：工具視窗、功能表和工具列，以及主視窗空間。 工具視窗停駐在應用程式視窗的左側和右側。 搜尋方塊、功能表列和標準工具列位於頂端。 當您載入方案或專案時，編輯器和設計工具會出現在應用程式視窗的中央區域。 在開發應用程式時，您大部分時間都會在此中央區域工作。

::: moniker-end

Visual Studio 會使用「專案」  來組織應用程式的程式碼，並使用「解決方案」  來組織專案。 專案包含用來建置您應用程式的所有選項、組態和規則。 它也會管理所有專案之檔案與任何外部檔案間的關聯性。 若要建立您的應用程式，請先建立新的專案和解決方案。

### <a name="to-create-a-console-app-project"></a>建立主控台應用程式專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]  ，開啟 [新增專案]  對話方塊。

   ![在功能表列上，選擇 [檔案] > [新增] > [專案]](../ide/media/get-started-cpp-file-new-project-menu.png)

1. 在 [新增專案]  對話方塊中，選取 [已安裝] > [Visual C++]  (如果尚未選取)。 在中央窗格中，選取 [Windows 主控台應用程式]  範本。 在 [名稱]  編輯方塊中，輸入 *HelloApp*。

   ![使用 [新增專案] 對話方塊來建立應用程式專案](../ide/media/get-started-cpp-new-project-dialog.png)

   根據已安裝的 Visual Studio 工作負載和元件，您的對話方塊可能會有不同的選擇。 如果看不到 Visual C++ 專案範本，則需要重新執行 Visual Studio 安裝程式，並安裝**使用 C++ 的桌面開發**工作負載。 您可以直接從 [新增專案]  對話方塊執行此作業。 若要啟動安裝程式，請選擇對話方塊上的 [開啟 Visual Studio 安裝程式]  連結。

1. 選擇 [確定]  按鈕，以建立應用程式專案和解決方案。

   這樣會建立 HelloApp 專案和解決方案以及 Windows 主控台應用程式的基本檔案，並自動載入 **方案總管**。 HelloApp.cpp  檔案會在程式碼編輯器中開啟。 這些項目會在方案總管  中出現：

   ![方案在方案總管中的所有檔案](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>將程式碼新增至應用程式

接下來，新增程式碼以在主控台視窗中顯示 "Hello" 文字。

### <a name="to-edit-code-in-the-editor"></a>在編輯器中編輯程式碼

1. 在 HelloApp.cpp  檔案的 `return 0;` 行之前輸入空白行，然後輸入下列程式碼：

   ```cpp
   cout << "Hello\n";
   ```

   `cout`底下會出現紅色曲線。 如果您將滑鼠指標停留在它上方，則會出現錯誤訊息。

   ![cout 的錯誤文字](../ide/media/get-started-cpp-intellisense-error.png)

   錯誤訊息也會出現在 [錯誤清單]  視窗中。 您可以在功能表列上選擇 [檢視] > [錯誤清單]  來顯示此視窗。

   ![[錯誤清單] 視窗中的錯誤](../ide/media/get-started-cpp-error-list.png)

   您的程式碼遺失 [std::cout](/cpp/standard-library/iostream) 的宣告，其位在 *\<iostream>* 標頭檔中。

1. 若要包含 iostream  標頭，請在 `#include "stdafx.h"` 後面輸入下列程式碼：

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   您可能會注意到在您輸入程式碼時會出現一個方塊。 此方塊包含您所輸入字元的自動完成建議。 它是 C++ IntelliSense 的一部分，可提供編碼提示，包含類別或介面成員和參數資訊。 您也可以使用程式碼片段，也就是預先定義的程式碼區塊。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md) 和[程式碼片段](../ide/code-snippets.md)。

   ![編輯器中的已修正程式碼](../ide/media/get-started-cpp-cout-fix.png)

   當您修正錯誤時， `cout` 底下的紅色曲線就會消失。

1. 若要將變更儲存至檔案，請按 **Ctrl+S**。

## <a name="build-the-app"></a>建置應用程式

建置程式碼十分輕鬆。 在功能表列上，選擇 [建置] > [建置解決方案]  。 Visual Studio 會建置 HelloApp 解決方案，並在 [輸出]  視窗中報告進度。

   ![建置 HelloApp 解決方案](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>偵錯和測試應用程式

您可以偵錯 HelloApp，看看 "Hello" 這個字是否出現在主控台視窗中。

### <a name="to-debug-the-app"></a>偵錯應用程式

若要啟動偵錯工具，請選擇功能表列上的 [偵錯] > [開始偵錯]  。

![[偵錯] 功能表上的 [開始偵錯] 命令](../ide/media/get-started-cpp-start-debugging-menu.png)

偵錯工具會啟動並執行程式碼。 主控台視窗 (外觀類似命令提示字元的另一個視窗) 會出現幾秒鐘，並在偵錯工具停止執行時快速關閉。 若要查看文字，則必須設定中斷點以停止程式執行。

### <a name="to-add-a-breakpoint"></a>若要加入中斷點

1. 在編輯器中，將資料指標放在 `return 0;` 行。 在功能表列上，選擇 [偵錯] > [切換中斷點]  。 您也可以按一下左邊界來設定中斷點。

     ![[偵錯] 功能表上的 [切換中斷點] 命令](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     在編輯器視窗最左緣、程式碼行的旁邊會出現一個紅色圓圈。

     ![視窗邊界中指出的中斷點](../ide/media/get-started-cpp-breakpoint-set.png)

1. 若要開始偵錯，請按 **F5**。

   偵錯工具隨即啟動，而主控台視窗會出現並顯示 **Hello**這個字。

   ![主控台視窗中的 Hello 文字](../ide/media/get-started-cpp-helloapp-window.png)

1. 若要停止偵錯，請按 **Shift+F5**。

如需主控台專案偵錯的詳細資訊，請參閱[主控台專案](../debugger/debugging-preparation-console-projects.md)。

## <a name="build-a-release-version-of-the-app"></a>建置應用程式的發行版本

既然已經驗證應用程式的運作一切正常，您就可以準備其發行組建。 發行組建會保留偵錯資訊，並使用編譯器最佳化選項來建立較小且更快速的程式碼。

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>清除方案檔案和建置發行版本

1. 在功能表列上，選擇 [建置] > [清除解決方案]  ，刪除在上一個建置期間建立的中繼檔和輸出檔。

   ![[建置] 功能表上的 [清除方案] 命令](../ide/media/get-started-cpp-clean-solution-menu.png)

1. 若要將 HelloApp 的方案組態從 [偵錯]  變更為 [發行]  ，請在工具列中選取 [解決方案組態] 控制項的下拉式清單，然後選擇 [發行]  。

   ![建置應用程式的發行版本](../ide/media/get-started-cpp-set-release-configuration.png)

1. 建置方案。 在功能表列上，選擇 [建置] > [建置解決方案]  。

此建置完成時，您已建立可在任何命令提示字元視窗中複製和執行的應用程式。 它可能不會執行太多作業，但為更高作業的閘道。

恭喜您完成此快速入門！

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio IDE 進行 C++ 桌面程式開發](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [逐步解說：使用 C# 或 Visual Basic 建立簡單的應用程式](../get-started/csharp/tutorial-wpf.md)
- [Visual Studio 中的生產力功能](../ide/productivity-features.md)
