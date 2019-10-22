---
title: 使用的C++跨平臺行動開發 |Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 61bb3e17b104759995852959a7396d5a76927cfb
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589047"
---
# <a name="cross-platform-mobile-development-with-c"></a>跨平臺行動裝置開發C++

您可以使用 Visual Studio C++中提供的跨平臺工具，建立 IOS、Android 和 Windows 裝置的原生應用程式。 **使用C++** 的行動裝置開發是 Visual Studio 安裝程式中可用的工作負載。 它會安裝適用于跨平臺開發共用程式庫和原生應用程式所需的 Sdk 和工具。 安裝時，您可以使用C++來建立可在 IOS 和 Android 裝置和平臺、windows、microsoft Store 和 Xbox 上執行的程式碼。

撰寫多個平臺的程式碼通常會令人沮喪。 適用於 iOS、Android 和 Windows 的主要開發語言和工具在每個平台上都不一樣。 不過，所有平台都支援使用 C++ 撰寫程式碼。 這是可讓您跨平臺重複使用核心程式代碼的常見分母。 使用 C++ 撰寫的原生程式碼效能更好，並可防止反向工程。 建立用於多個平台的應用程式時，重複使用程式碼可以節省時間和精力。

使用C++進行跨平臺行動開發的開發有數個優點：

- **安裝簡單。** Visual Studio 安裝程式會取得並安裝建置 Android 和 iOS 應用程式或文件庫所需要的協力廠商工具和 SDK。 設定和安裝很簡單，而且大部分都是自動的。

- **功能強大且熟悉的建置環境。** 使用 Visual Studio 範本輕鬆建立可共用的跨平台解決方案和專案。 使用通用介面管理所有專案的屬性。 使用 Visual Studio 編輯器編輯所有的程式碼，並利用內建的跨平台 IntelliSense 完成程式碼及醒目提示錯誤。

- **一致的偵錯體驗。** 在 Visual Studio 中使用世界級的偵錯工具，即可在所有平臺C++上觀看並逐步執行程式碼： Android 裝置和模擬器、iOS 模擬器和裝置，以及 Windows 或 windows 儲存裝置和模擬器。

## <a name="get-the-tools"></a>取得工具

使用C++的行動裝置開發是 Visual Studio 隨附的可安裝工作負載。 如需必要條件和安裝指示，請參閱[使用C++安裝跨平臺](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)行動裝置開發。 若要建置 iOS 程式碼，您也需要 Mac 電腦和 Apple iOS 開發人員帳戶。 如需詳細資訊，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。

## <a name="come-up-to-speed"></a>加速前進

如果您原來使用的是 Android 或 iOS 程式開發，我們有一些很棒的材料協助您開始使用。 Visual Studio 是出色且強大的開發環境。 若要了解如何使用它，請嘗試 [Android 開發人員快速入門](/previous-versions/windows/apps/dn275875\(v=win.10\))或 [iOS 開發人員快速入門](/previous-versions/windows/apps/jj657966\(v=win.10\))。 這些文章將為您介紹如何 Visual Studio，以及開發適用于 Windows 和 Windows Store 的跨平臺應用程式所需的概念。 若要開始撰寫第一個 iOS 和 Android 的跨平臺應用程式，請參閱[在 Android 和 iOS 上建立 OPENGL ES 應用程式](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)。

具有工作負載的C++行動裝置開發包含數個範本，可協助您開始使用您的應用程式：

- OpenGLES 2 應用程式 (Android、iOS、Windows 通用)

  建立一個方案來包含一組用以建置 Android Native Activity 應用程式、iOS 應用程式和通用 Windows 應用程式的專案，以及共用的 C++ 程式碼程式庫。 這些應用程式使用以通用 C++ OpenGL ES 程式碼所建立的平台特定程式庫，在每個應用程式中繪製相同的旋轉立方體。 若要使用此範本，請在安裝 Visual Studio 時包含**通用 Windows 平臺開發**工作負載。

- Native-Activity 應用程式 (Android)

  建立完整的 C++ OpenGL 應用程式做為 Android Native Activity 專案。

- OpenGLES 應用程式 (Android、iOS)

  建立具有一組專案的解決方案，以建置 Android Native Activity 應用程式和 iOS 應用程式。 這些應用程式使用以通用 C++ OpenGL ES 程式碼所建立的平台特定程式庫，在每個應用程式中繪製相同的旋轉立方體。

- 共用程式庫 (Android、iOS)

  建立具有專案的解決方案，使用通用的 C++ 程式碼在共用的專案中建立 Android 動態程式庫 (.so) 檔案和 iOS 靜態程式庫 (.a) 檔案。

- 基本應用程式 (Android、Ant)

  建立一個 Android "Hello, World" 應用程式專案，其中只使用 Java 原始碼和 Ant 組建系統。

- 基本應用程式 (Android、Gradle)

  建立一個 Android "Hello, World" 應用程式專案，其中只使用 Java 原始碼和 Gradle 組建系統。

- 基本程式庫 (Android、Ant)

  建立一個 Android "Hello, World" 程式庫專案，其中只使用 Java 原始碼和 Ant 組建系統。

- 基本程式庫 (Android、Gradle)

  建立一個 Android "Hello, World" 程式庫專案，其中只使用 Java 原始碼和 Gradle 組建系統。

- 動態共用程式庫 (Android)

  使用 C++ 程式碼建立 Android 動態程式庫 (.so) 檔案。

- OpenGLES 2 應用程式 (iOS)

  建立一個方案，其中含有一組用以建置 OpenGL ES 2 iOS 應用程式的專案。 應用程式會使用 C++ OpenGL ES 程式碼的程式庫，來繪製 iOS 應用程式中的旋轉立方體。 若想了解如何將 C++ 程式庫匯入 iOS 應用程式，這個應用程式是一個最佳起點。

- 靜態程式庫 (Android)

  建立專案以建置 Android 靜態程式庫。 您只能連結 Android 應用程式的一個動態程式庫，但可以連結任何數目的靜態程式庫。

- 靜態程式庫 (iOS)

  建立專案以建置 iOS 靜態程式庫。

- Makefile 專案 (Android)

  為自己的 Android Makefile 專案建立專案包裝函式。

## <a name="try-out-sample-code"></a>試驗範例程式碼

下載範例，示範如何建立可在 Windows、Android 和 iOS 應用程式中使用的共用程式碼程式庫。 和，請參閱如何建立適用于 Android 的完整原生活動應用程式的範例。 若要開始使用，請參閱[跨平台行動裝置應用程式開發範例](../cross-platform/cross-platform-mobile-development-examples.md)。

## <a name="see-also"></a>請參閱

[使用C++ \ 安裝跨平臺行動開發](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
[安裝和設定工具以使用 iOS \ 建立](../cross-platform/install-and-configure-tools-to-build-using-ios.md)
[建立 Android native activity 應用程式](../cross-platform/create-an-android-native-activity-app.md)\
[在 Android 和 iOS 上建立 OPENGL ES 應用程式](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)\
[跨平台行動裝置應用程式開發範例](../cross-platform/cross-platform-mobile-development-examples.md)
