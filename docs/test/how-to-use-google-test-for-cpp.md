---
title: 如何使用 C++ 的 Google Test
description: 在 Visual Studio 中使用 Google Test 來建立 C++ 單元測試。
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042960"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Google Test

在 Visual Studio 2017 及更新版本中，Google Test 已作為 [使用 C++ 進行桌面開發] 工作負載的預設元件，與 Visual Studio IDE 整合。 若要確認已安裝在您的電腦上，請開啟 Visual Studio 安裝程式，並在工作負載元件清單下尋找 Google Test：

![安裝 Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中新增 Google Test 專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案節點，然後選擇 [ **加入** > **新專案**]。
2. 將 [語言] 設為 [C++]，然後在搜尋方塊中鍵入 **test**。 從結果清單中，選擇 **Google Test 專案**。
3. 提供測試專案名稱，然後按一下 [確定]。

![新增 Google Test 專案](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中新增 Google Test 專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案節點，然後選擇 [ **加入** > **新專案**]。
2. 在左窗格中，選擇 [ **Visual C++** > **測試** ]，然後在中間窗格中選擇 [ **Google Test 專案** ]。
3. 提供測試專案名稱，然後按一下 [確定]。

![新增 Google Test 專案](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>設定測試專案

在出現的 [測試專案組態] 對話方塊中，您可以選擇要測試的專案。 當您選擇專案時，Visual Studio 會加入所選專案的參考。 如果您未選擇任何專案，則需要以手動方式加入要測試之專案的參考。 在 Google Test 二進位檔的靜態和動態連結之間選擇時，所有 C++ 程式的考量都相同。 如需詳細資訊，請參閱 [Visual C++ 中的 DLL](/cpp/build/dlls-in-visual-cpp)。

![設定 Google Test 專案](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>設定其他選項

從主功能表中，選擇 [**工具**  >  **選項**]  >  **適用於 Google Test 的測試配接器** 以設定其他選項。 如需這些設定的詳細資訊，請參閱 Google Test 文件。

![Google Test 專案設定](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>新增 include 指示詞

在您的測試 *.cpp* 檔案中，加入所需的任何指示詞， `#include` 讓測試程式碼可以看到程式的類型和函式。 一般而言，此程式會在資料夾階層中上移一層。 如果您鍵入 `#include "../"`，IntelliSense 視窗會隨即出現並讓您選取標頭檔的完整路徑。

![新增 #include 指示詞](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>撰寫及執行測試

您現在準備好撰寫及執行 Google Test。 如需測試宏的相關資訊，請參閱 [Google Test 入門](https://github.com/google/googletest/blob/master/docs/primer.md) 。 如需使用 **測試總管** 探索、執行及分組測試的資訊，請參閱 [使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱

[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
