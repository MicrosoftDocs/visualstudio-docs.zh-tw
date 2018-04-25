---
title: 如何在 Visual Studio 中使用 C++ 的 CTest | Microsoft Docs
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 5956c605eb838721185598d4c5713c59164db071
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 CTest

根據預設，CMake (包括 CTest) 已整合到 Visual Studio IDE 作為 [使用 C++ 的桌面開發] 工作負載的元件。 如果您需要將它安裝在您的電腦上，請開啟 Visual Studio 安裝程式，按一下 [修改] 按鈕，並在工作負載元件清單下查看[適用於 Visual C++ 的 CMake 工具](/cpp/ide/cmake-tools-for-visual-cpp)。

## <a name="to-write-tests"></a>撰寫測試

Visual Studio 中的 CMake 支援不包括 Visual Studio 專案系統。 因此，您會像是在任何 CMake 環境中一樣，撰寫並設定 CTest 測試。 如需在 Visual Studio 中使用 CMake 的詳細資訊，請參閱[適用於 Visual C++ 的 CMake 工具](/cpp/ide/cmake-tools-for-visual-cpp)。

## <a name="to-run-tests-visual-studio-2017-version-156"></a>執行測試 (Visual Studio 2017 15.6 版)

在 Visual Studio 2017 15.6 版中，CTest 已與 [測試總管] 完全整合，並同時支援 Google 和 Boost 單元測試架構。 根據預設，那些架構會以元件的形式包含在 [使用 C++ 的桌面開發] 工作負載中。 不過，如果您是從舊版的 Visual Studio 升級專案，則可能需要使用 Visual Studio 安裝程式來安裝這些架構。

下圖顯示使用 Google 測試架構的 CTest 執行結果：

![VS2017 15.6 中使用 Google 測試架構的 CTest](media/ctest-test-explorer.png "[測試總管] 中的 CTest 和 Google 測試")

如果您是使用 CTest 而非 Google 或 Boost 配接器，便會看到 CTest 層級的結果，而不是個別測試方法層級的結果。 您可以偵錯並逐步執行僅限 CTest 可執行檔，但不支援個別測試上的堆疊追蹤。

## <a name="to-run-tests-visual-studio-2017-version-155"></a>執行測試 (Visual Studio 2017 15.5 版)

在 **Visual Studio 2017 15.5 版**中，CTest 目前尚未與 [測試總管] 整合。 您可以從 CMake 主功能表執行測試，或從**方案總管**中 **CMakeLists.txt** 檔案的操作功能表執行測試。 測試結果會被導向至 Visual Studio 的 [輸出視窗]。

![在 VS2017 15.5 中執行 CTest 測試](media/cpp-cmake-run-tests.png "在 15.5 中執行 CTest 測試")

## <a name="see-also"></a>另請參閱

[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)