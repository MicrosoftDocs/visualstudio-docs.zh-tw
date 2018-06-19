---
title: 建立 Android Native Activity 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 51555b660b51c227dd7c80da04f2eecd699c5c96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31066121"
---
# <a name="create-an-android-native-activity-app"></a>建立 Android Native Activity 應用程式
當您安裝適用於跨平台行動裝置開發的 Visual C++ 選項時，Visual Studio 2015 可用來建立功能完整的 Android Native Activity 應用程式。 Android 原生開發套件 (NDK) 是一個可讓您實作大部分完全使用 C/C++ 程式碼之 Android 應用程式的工具集。 一些 Java JNI 程式碼可做為讓 C/C++ 程式碼與 Android 互動的黏著劑。 Android NDK 引進了使用 Android 應用程式開發介面層級 9 建立 Native Activity 應用程式的功能。 Native Activity 程式碼在建立使用 Unreal 引擎或 OpenGL 的遊戲和圖形密集應用程式方面很受歡迎。 本主題會引導您建立使用 OpenGL 的簡易 Native Activity 應用程式。 其他主題會引導您逐步了解開發人員編輯、建置、偵錯和部署 Native Activity 程式碼的週期。  
  
 [需求](#req)   
 [建立新的 Native Activity 專案](#Create)   
 [建置並執行預設 Android Native Activity 應用程式](#BuildHello)  
  
##  <a name="req"></a> 需求  
 請先確認您已符合所有系統需求，並已在 Visual Studio 2015 中安裝適用於跨平台行動裝置開發的 Visual C++，才能建立新的專案。 如需詳細資訊，請參閱 [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)。 請確認安裝包含所需之協力廠商工具和 SDK，並已安裝 Visual Studio Emulator for Android。  
  
##  <a name="Create"></a> 建立新的 Native Activity 專案  
 在本教學課程中，您會建立新的 Android Native Activity 專案，然後在 Visual Studio Emulator for Android 中建置並執行預設的應用程式。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  開啟 Visual Studio。 在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在 [新增專案]  對話方塊中的 [範本] 底下，選擇 [Visual C++] 、[跨平台] ，然後選擇 [Native-Activity 應用程式 (Android)]  範本。  
  
3.  指定像是 `MyAndroidApp` 的應用程式名稱，然後選擇 [確定]。  
  
     ![建立 Native Activity 專案](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")  
  
     Visual Studio 會建立新的方案，並開啟方案總管。  
  
     ![[方案總管] 中的 Native Activity 專案](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
 新的 Android Native Activity 應用程式方案包含兩個專案：  
  
-   **MyAndroidApp.NativeActivity** 包含參考和黏附程式碼 (glue code)，可讓您的應用程式當做 Native Activity 在 Android 上執行。 黏合程式碼 (glue code) 的進入點實作位於 main.cpp 中。 先行編譯標頭檔位於 pch.h 中。 這個 Native Activity 應用程式專案會編譯至封裝專案所挑選的共用程式庫 .so 檔案中。  
  
-   **MyAndroidApp.Packaging** 會建立部署在 Android 裝置或模擬器上時所使用的 .apk 檔案。 其中包含資源以及您設有資訊清單屬性的 AndroidManifest.xml 檔案。 其中也包含用來控制建置流程的 build.xml 檔案。 依預設，它會設成啟始專案，以便直接從 Visual Studio 部署及執行。  
  
##  <a name="BuildHello"></a> 建置並執行預設 Android Native Activity 應用程式  
 建置並執行範本所產生的應用程式，以驗證您的安裝和設定。 針對這個初始測試，在 Visual Studio Emulator for Android 安裝的其中一個裝置設定檔上執行應用程式。 如果您想要在其他目標上測試您的應用程式，您可以載入目標模擬器，或將裝置連接至您的電腦。  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>建置並執行預設 Native Activity 應用程式  
  
1.  若尚未選取，請從 [方案平台]  下拉式清單中選擇 [x86]  。  
  
     ![[方案平台] 下拉式清單中的 x86 選項](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     如果未顯示 [方案平台] 清單，請從 [新增或移除按鈕] 下拉式清單中選擇 [x86]，然後選擇您的平台。  
  
2.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
     [輸出] 視窗會顯示方案中這兩個專案的建置流程輸出。  
  
3.  選擇其中一個 VS Emulator Android Phone (x86) 做為部署目標。  
  
     如果您已經安裝其他模擬器或連接 Android 裝置，就可以在部署目標下拉式清單中加以選擇。  
  
4.  按 F5 啟動偵錯，或按 Shift+F5 啟動但不偵錯。  
  
     以下是預設應用程式在 Visual Studio Emulator for Android 中的外觀。  
  
     ![執行您應用程式的模擬器](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio 啟動模擬器，這需要幾秒的時間來載入及部署您的程式碼。 在您的應用程式啟動之後，您可以設定中斷點，並使用偵錯工具，以逐步執行程式碼、檢查本機及監看值。  
  
5.  按 Shift + F5 停止偵錯。  
  
     模擬器是分開的程序，會繼續執行。 您可以將程式碼多次編輯、編譯及部署至相同的模擬器。