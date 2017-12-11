---
title: "如何在 Visual Studio 中使用 C++ 的 Google Test | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4868fae-fd6d-4b98-a85f-f23b0dd2fca5
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 917b0f0bc65ba4b0306a8bec12d7fd98ee540e34
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Google Test
在 **Visual Studio 2017 15.5 版**和更新版本中，Google Test 已整合到 Visual Studio IDE 作為 [使用 C++ 的桌面開發] 工作負載的預設元件。 若要確認已安裝在您的電腦上，請開啟 Visual Studio 安裝程式，並在工作負載元件清單下尋找 Google Test：

![安裝 Google Test](media/cpp-gtest-install.png "安裝 C++ 的 Google Test")

## <a name="add-a-google-test-project-to-the-solution"></a>將 Google Test 專案新增至方案
1. 在**方案總管**中，以滑鼠右鍵按一下方案節點，然後選擇 [新增] | [新增專案]。 
2. 在左窗格中選擇 [Visual C++] | [測試]，然後在中間窗格中選擇 **Google Test 專案**。 
3. 提供測試專案名稱，然後按一下 [確定]。 

![新增 Google Test 專案](media/cpp-gtest-new-project.png "新增 Google Test 專案")

## <a name="configure-the-test-project"></a>設定測試專案
在出現的 [測試專案組態] 對話方塊中，您可以選擇要測試的專案。 當您選擇專案時，Visual Studio 會加入所選專案的參考。 如果您未選擇任何專案，則需要以手動方式加入要測試之專案的參考。 在 Google Test 二進位檔的靜態和動態連結之間選擇時，所有 C++ 程式的考量都相同。 如需詳細資訊，請參閱 [Visual C++ 中的 DLL](/cpp/build/dlls-in-visual-cpp)。 

 ![設定 Google Test 專案](media/cpp-gtest-config.png "設定 Google Test 專案")

## <a name="set-additional-options"></a>設定其他選項
從主功能表選擇 [工具] | [選項] | [適用於 Google Test 的測試配接器]，以設定其他選項。 如需這些設定的詳細資訊，請參閱 Google Test 文件。

 ![Google Test 專案設定](media/cpp-gtest-settings.png "Google Test 專案設定")

## <a name="add-include-directives"></a>新增 include 指示詞
在測試的 .cpp 檔中，新增任何需要的 `#include` 指示詞，以便測試程式碼可以看到程式的類型和函式。 一般而言，此程式會在資料夾階層中上移一層。 如果您鍵入 `#include "../"`，IntelliSense 視窗會隨即出現並讓您選取標頭檔的完整路徑。

![新增 #include 指示詞](media/cpp-gtest-includes.png "將 include 指示詞新增至測試的 .cpp 檔")

## <a name="write-and-run-tests"></a>撰寫及執行測試
您現在準備好撰寫及執行 Google Test。 如需測試巨集的資訊，請參閱 [Google Test 入門](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md)。 如需使用**測試總管**探索、執行及分組測試的資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱
[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)


  







