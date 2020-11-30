---
title: 如何使用 C++ 的 CTest
description: 瞭解如何使用 CTest （預設已整合至 Visual Studio IDE）來建立和執行測試。
ms.custom: SEO-VS-2020
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5ed713e8b216d64816abd9e25d4d84ce53c44499
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329987"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>如何在 Visual Studio 2017 及更新版本中使用 C++ 的 CTest

根據預設，CMake (包括 CTest) 已整合到 Visual Studio IDE 中，作為 **「使用 C++ 的桌面開發」** 工作負載的元件。 若您需要在您的電腦上安裝它，請開啟 Visual Studio 安裝程式，按一下 [使用 C++ 進行桌面開發] 按鈕，然後按一下 [修改]。 在工作負載元件清單的下方選取 [適用於 Windows 的 C++ CMake 工具]。

## <a name="to-write-tests"></a>撰寫測試

Visual Studio 中的 CMake 支援不包括 Visual Studio 專案系統。 因此，您會像是在任何 CMake 環境中一樣，撰寫並設定 CTest 測試。 使用 `enable_testing()` 命令來啟用測試，並使用 `add_test()` 或 `gtest_discover_tests()` 命令來加入新的測試。 若要深入瞭解 CTest，請參閱 [CMake 檔](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest)。 

如需在 Visual Studio 中使用 CMake 的詳細資訊，請參閱 [Visual Studio 中的 CMake 專案](/cpp/build/cmake-projects-in-visual-studio)。

## <a name="to-run-tests"></a>執行測試

CTest 已與 [測試總管] 完全整合，並同時支援 Google 和 Boost 單元測試架構。 根據預設，那些架構會以元件的形式包含在 **「使用 C++ 的桌面開發」** 工作負載中。 不過，如果您是從舊版的 Visual Studio 升級專案，則可能需要使用 Visual Studio 安裝程式來安裝這些架構。

下圖顯示使用 Google 測試架構的 CTest 執行結果：

![Visual Studio 中的 CTest 和 Google Test 架構](media/ctest-test-explorer.png)

如果您是使用 CTest 而非 Google 或 Boost 配接器，便會看到 CTest 層級的結果，而不是個別測試方法層級的結果。 您可以偵錯並逐步執行僅限 CTest 可執行檔，但不支援個別測試上的堆疊追蹤。

## <a name="see-also"></a>另請參閱

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
