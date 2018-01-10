---
title: "如何在 Visual Studio 中使用 C++ 的 CTest | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 989f2b06df55fd0927863fe7e5603d3d0ec90b06
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 CTest
CMake (包括 CTest) 已整合到 Visual Studio IDE 作為 [使用 C++ 的桌面開發] 工作負載的元件。 若要將它安裝在您的電腦上，請開啟 Visual Studio 安裝程式，並在工作負載元件清單下尋找 [適用於 Visual C++ 的 CMake 工具](/cpp/ide/cmake-tools-for-visual-cpp)。

Visual Studio 中的 CMake 支援不包括 Visual Studio 專案系統。 因此，您會像是在任何 CMake 環境中一樣，撰寫並設定 CTest 測試。 如需在 Visual Studio 中使用 CMake 的詳細資訊，請參閱[適用於 Visual C++ 的 CMake 工具](/cpp/ide/cmake-tools-for-visual-cpp)。

**Visual Studio 2017 15.5 版** 的 CTest 目前未與**測試總管**整合。 您可以從 CMake 主功能表執行測試，或從**方案總管**中 **CMakeLists.txt** 檔案的操作功能表執行測試。 測試結果會被導向至 Visual Studio 的 [輸出視窗]。

![執行 CTest 測試](media/cpp-cmake-run-tests.png "執行 CTest 測試")


## <a name="see-also"></a>請參閱
[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)


  







