---
title: 適用於跨平台行動裝置開發的 Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 00f5bcdbdd84de3a33914d3ea90f4eb00c960f1f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>適用於跨平台行動裝置開發的 Visual C++
您可以建置 iOS、Android 和 Windows 裝置的原生 C++ 應用程式，以及使用跨平台行動裝置開發的 Visual C++，在為 iOS、Android 和 Windows 建置的程式庫中共用通用程式碼。 這是為共用程式庫和原生應用程式的跨平台開發工具安裝了所需 SDK 和工具的 Visual Studio 2015 提供的選項。 安裝好後，您就可以使用 Visual C++ 建立程式碼，除了 Windows、Windows Phone 和 Xbox 之外，還可在 iOS 和 Android 裝置及平台上執行。  
  
 針對多個平台撰寫程式碼很令人沮喪。 適用於 iOS、Android 和 Windows 的主要開發語言和工具在每個平台上都不一樣。 不過，所有平台都支援使用 C++ 撰寫程式碼。 這是您可以跨平台重複使用核心程式碼的共同點。 使用 C++ 撰寫的原生程式碼效能更好，並可防止反向工程。 建立用於多個平台的應用程式時，重複使用程式碼可以節省時間和精力。  
  
 使用適用於跨平台行動裝置開發的 Visual C++ 進行程式開發有數項優勢：  
  
1.  **安裝簡單。** Visual Studio 安裝程式會取得並安裝建置 Android 和 iOS 應用程式或文件庫所需要的協力廠商工具和 SDK。 組態與設定既簡單又多為自動化。  
  
2.  **功能強大且熟悉的建置環境。** 使用 Visual Studio 範本輕鬆建立可共用的跨平台解決方案和專案。 使用通用介面管理所有專案的屬性。 使用 Visual Studio 編輯器編輯所有的程式碼，並利用內建的跨平台 IntelliSense 完成程式碼及醒目提示錯誤。  
  
3.  **一致的偵錯體驗。** 使用 Visual Studio 中的世界級偵錯工具在所有平台上監看和逐步執行 C++ 程式碼，包括 Android 裝置和模擬器、iOS 模擬器和裝置，以及 Windows 或 Windows Phone 裝置和模擬器。  
  
## <a name="get-the-tools"></a>取得工具  
 適用於跨平台行動裝置開發的 Visual C++ 是隨附於 Visual Studio 2015 的可安裝選項。 如需必要條件和安裝指示，請參閱 [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)。 若要建置 iOS 程式碼，您也需要 Mac 電腦和 Apple iOS 開發人員帳戶。 如需詳細資訊，請參閱 [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。  
  
## <a name="come-up-to-speed"></a>加速前進  
 如果您原來使用的是 Android 或 iOS 程式開發，我們有一些很棒的材料協助您開始使用。 Visual Studio 是出色且強大的開發環境。 若要了解如何使用它，請嘗試 [Android 開發人員快速入門](/previous-versions/windows/apps/dn275875\(v=win.10\)) 或 [iOS 開發人員快速入門](/previous-versions/windows/apps/jj657966\(v=win.10\))。 這些主題會為您介紹 Visual Studio 和開發 Windows 和 Windows Phone 跨平台應用程式所需要的概念。 若要開始撰寫第一個 iOS 和 Android 跨平台應用程式，請參閱 [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)。  
  
 適用於跨平台行動裝置開發的 Visual C++ 包含數個範本，可幫助您開始建立應用程式：  
  
-   OpenGLES 2 應用程式 (Android、iOS、Windows 通用)  
  
     建立一個方案來包含一組用以建置 Android Native Activity 應用程式、iOS 應用程式和通用 Windows 應用程式的專案，以及共用的 C++ 程式碼程式庫。 這些應用程式使用以通用 C++ OpenGL ES 程式碼所建立的平台特定程式庫，在每個應用程式中繪製相同的旋轉立方體。 當您安裝 Visual Studio 來使用此範本時，您必須包含 [通用 Windows 應用程式開發工具] 選項。  
  
-   Native-Activity 應用程式 (Android)  
  
     建立完整的 C++ OpenGL 應用程式做為 Android Native Activity 專案。  
  
-   OpenGLES 應用程式 (Android、iOS)  
  
     建立具有一組專案的解決方案，以建置 Android Native Activity 應用程式和 iOS 應用程式。 這些應用程式使用以通用 C++ OpenGL ES 程式碼所建立的平台特定程式庫，在每個應用程式中繪製相同的旋轉立方體。  
  
-   共用程式庫 (Android、iOS)  
  
     建立具有專案的解決方案，使用通用的 C++ 程式碼在共用的專案中建立 Android 動態程式庫 (.so) 檔案和 iOS 靜態程式庫 (.a) 檔案。  
  
-   基本應用程式 (Android、Ant)  
  
     建立一個 Android "Hello, World" 應用程式專案，其中只使用 Java 原始碼和 Ant 組建系統。  
  
-   基本應用程式 (Android、Gradle)  
  
     建立一個 Android "Hello, World" 應用程式專案，其中只使用 Java 原始碼和 Gradle 組建系統。  
  
-   基本程式庫 (Android、Ant)  
  
     建立一個 Android "Hello, World" 程式庫專案，其中只使用 Java 原始碼和 Ant 組建系統。  
  
-   基本程式庫 (Android、Gradle)  
  
     建立一個 Android "Hello, World" 程式庫專案，其中只使用 Java 原始碼和 Gradle 組建系統。  
  
-   動態共用程式庫 (Android)  
  
     使用 C++ 程式碼建立 Android 動態程式庫 (.so) 檔案。  
  
-   OpenGLES 2 應用程式 (iOS)  
  
     建立一個方案，其中含有一組用以建置 OpenGL ES 2 iOS 應用程式的專案。 應用程式會使用 C++ OpenGL ES 程式碼的程式庫，來繪製 iOS 應用程式中的旋轉立方體。 若想了解如何將 C++ 程式庫匯入 iOS 應用程式，這個應用程式是一個最佳起點。  
  
-   靜態程式庫 (Android)  
  
     建立專案以建置 Android 靜態程式庫。 您只能連結 Android 應用程式的一個動態程式庫，但可以連結任何數目的靜態程式庫。  
  
-   靜態程式庫 (iOS)  
  
     建立專案以建置 iOS 靜態程式庫。  
  
-   Makefile 專案 (Android)  
  
     為自己的 Android Makefile 專案建立專案包裝函式。  
  
## <a name="try-out-sample-code"></a>試驗範例程式碼  
 下載範例，示範如何建立可用在 Windows、Android 和 iOS 應用程式中的共用程式碼程式庫，以及如何建立完整的 Android Native Activity 應用程式。 若要開始使用，請參閱 [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
1.  [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [建立 Android Native Activity 應用程式](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md)