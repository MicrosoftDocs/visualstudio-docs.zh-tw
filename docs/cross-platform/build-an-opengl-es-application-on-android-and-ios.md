---
title: 在 Android 和 iOS 上建置 OpenGL ES 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: aa8ffe308f8a1181ed18af52ba7537c46007de94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317643"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>在 Android 和 iOS 上建置 OpenGL ES 應用程式

您可以針對共用通用程式碼的 iOS 應用程式與 Android 應用程式，建立 Visual Studio 方案和專案。 本文引導您完成可建立一個簡單的 iOS 應用程式和一個 Android Native Activity 應用程式的方案範本。 這兩個應用程式有通用的 C++ 程式碼，該程式碼使用 OpenGL ES 在每個平台上顯示相同的動畫旋轉立方體。 OpenGL ES (適用於內嵌系統的 OpenGL 或 GLES) 是受到許多行動裝置支援的 2D 和 3D 圖形 API。

## <a name="requirements"></a>需求

在您建立適用於 iOS 和 Android 的 OpenGL ES 應用程式之前，請確定符合所有系統需求。 否則，請安裝 Visual Studio Installer 中的「使用 C++ 進行行動開發」工作負載。 若要針對 iOS 建置，請納入選用的 C++ iOS 開發工具。 若要針對 Android 建置，請安裝 C++ Android 開發工具和所需的協力廠商工具：Android NDK、Apache Ant、Google Android Emulator 和 Intel Hardware Accelerated Execution Manager。 接下來，設定 Intel HAXM 和 Android Emulator，以便在您的系統上執行。 如需詳細資訊和詳細指示，請參閱[針對跨平台行動裝置應用程式開發安裝 Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)。 若要建置及測試 iOS 應用程式，您需要一部已根據安裝指示設定的 Mac 電腦。 如需如何設定 iOS 開發環境的詳細資訊，請參閱[I安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)

## <a name="create-a-new-opengles-application-project"></a>建立新的 OpenGLES 應用程式專案

在本教學課程中，您會先建立新的 OpenGL ES 應用程式專案，然後在 Visual Studio Emulator for Android 中建置並執行預設的應用程式。 接下來，您會建置適用於 iOS 的應用程式，然後在 iOS 裝置上執行該應用程式。

1. 在 Visual Studio 中，選擇 [檔案]   > [新增]   > [專案]  。

1. 在 [新增專案]  對話方塊的 [範本]  底下，選擇 [Visual C++]   > [跨平台]  ，然後選擇 [OpenGLES 應用程式 (Android、iOS)]  範本。

1. 指定像是 `MyOpenGLESApp` 的應用程式名稱，然後選擇 [確定]  。

   ![新的 OpenGLES 應用程式專案](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio 會建立新的方案，並開啟方案總管。

   ![[方案總管] 中的 MyOpenGLESApp](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   新的 OpenGL ES 應用程式方案包含三個程式庫專案和兩個應用程式專案。 [程式庫] 資料夾包含共用程式碼專案，以及參考共用程式碼的兩個平台專屬專案：

- `MyOpenGLESApp.Android.NativeActivity` 包含參考和黏附程式碼，可讓您的應用程式當作 Native Activity 在 Android 上實作。 黏附程式碼的進入點是在 *main.cpp* 中實作的，其中包含 `MyOpenGLESApp.Shared` 中共用的通用程式碼。 先行編譯標頭檔位於 *pch.h* 中。 這個 Native Activity 應用程式專案會編譯至 `MyOpenGLESApp.Android.Packaging` 專案所挑選的共用程式庫 ( *.so*) 檔案中。

- `MyOpenGLESApp.iOS.StaticLibrary` 會建立 iOS 靜態程式庫 ( *.a*) 檔案，其中包含 `MyOpenGLESApp.Shared`中的共用程式碼。 它會連結到由 `MyOpenGLESApp.iOS.Application` 專案所建立的應用程式。

- `MyOpenGLESApp.Shared` 包含可跨平台運作的共用程式碼。 它使用前置處理器巨集來進行平台專屬程式碼的條件式編譯。 共用程式碼會由 `MyOpenGLESApp.Android.NativeActivity` 與 `MyOpenGLESApp.iOS.StaticLibrary` 中的專案參考挑選。

該方案包含兩個專案，分別為 Android 和 iOS 平台建置應用程式：

- `MyOpenGLESApp.Android.Packaging` 會建立部署在 Android 裝置或模擬器上時所使用的 *.apk* 檔案。 此檔案中包含資源以及您設定資訊清單屬性所在的 AndroidManifest.xml 檔案。 其中也包含用來控制建置流程的 *build.xml* 檔案。 依預設，它會設成啟始專案，以便直接從 Visual Studio 部署及執行。

- **MyOpenGLESApp.iOS.Application** 包含資源和 Objective-C 黏附程式碼，以建立連結至 `MyOpenGLESApp.iOS.StaticLibrary` 中 C++ 靜態程式庫程式碼的 iOS 應用程式。 這個專案會建立組建套件，並由 Visual Studio 和遠端代理程式傳輸到您的 Mac。 當您建置這個專案時，Visual Studio 會傳送檔案和命令，以在 Mac 上建置及部署應用程式。

## <a name="build-and-run-the-android-app"></a>建置並執行 Android 應用程式

範本所建立的方案會將 Android 應用程式設定為預設專案。  您可以建置並執行這個應用程式，以確認您的安裝和設定。 針對初始測試，在 Android 版模擬器安裝的其中一個裝置設定檔上執行應用程式。 如果您想要在其他目標上測試您的應用程式，您可以載入目標模擬器，或將裝置連接至您的電腦。

### <a name="to-build-and-run-the-android-native-activity-app"></a>建置並執行 Android Native Activity 應用程式

1. 如果尚未選取，請從 [方案平台]  下拉式清單中選擇 [x86]  。

   ![將方案平台設為 x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   使用 x86 將目標設定為模擬器。 若要將目標設定為裝置，請根據裝置處理器來選擇方案平台。 如果未顯示 [方案平台]  清單，請從 [新增或移除按鈕]  清單中選擇 [方案平台]  ，然後選擇您的平台。

1. 在 [方案總管]  中，開啟 `MyOpenGLESApp.Android.Packaging` 專案的捷徑功能表，然後選擇 [建置]  。

   ![建置 Android 封裝專案](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   [輸出] 視窗會顯示 Android 共用程式庫和 Android 應用程式的建置流程輸出。

   ![建置 Android 專案輸出](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. 選擇其中一個模擬的 Android 裝置設定檔作為部署目標。

   ![選擇部署目標](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   如果您已經安裝其他模擬器或連接 Android 裝置，就可以在部署目標下拉式清單中加以選擇。 若要執行應用程式，所建置的方案平台必須符合目標裝置的平台。

1. 按 F5 啟動偵錯，或按 Shift+F5 啟動但不偵錯。

   Visual Studio 會啟動模擬器，這需要幾秒的時間來載入及部署您的程式碼。 以下是應用程式出現在模擬器中的方式：

   ![在 Android 模擬器中執行的應用程式](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   在您的應用程式啟動之後，您可以設定中斷點，並使用偵錯工具，以逐步執行程式碼、檢查本機及監看值。

1. 按 **Shift**+**F5** 停止偵錯。

   模擬器是分開的程序，會繼續執行。 您可以將程式碼多次編輯、編譯及部署至相同的模擬器。 您的應用程式會出現在模擬器的應用程式集合中，並可由此直接啟動。

   產生的 Android Native Activity 應用程式和程式庫專案會將 C++ 共用程式碼放在動態程式庫中，該程式庫包含「黏附」程式碼以與 Android 平台連接。 大多數應用程式程式碼會位於程式庫中，而資訊清單、資源和建置指令則會位於封裝專案中。 共用程式碼會從 NativeActivity 專案中的 main.cpp 呼叫。 如需如何對 Android Native Activity 進行程式設計的詳細資訊，請參閱 Android 開發人員 NDK 的 [概念](https://developer.android.com/ndk/guides/concepts.html) 頁面。

   Visual Studio 建置 Android Native Activity 專案的方式，是透過使用 Clang 做為平台工具組的 Android NDK。 Visual Studio 會將 NativeActivity 專案中的屬性對應至目標平台上用來編譯、連結及偵錯的選項。 如需詳細資料，請開啟 MyOpenGLESApp.Android.NativeActivity 專案的 [屬性頁]  對話方塊。 如需有關命令列參數的詳細資訊，請參閱 [Clang Compiler 使用者手冊](http://clang.llvm.org/docs/UsersManual.html)。

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>在 iOS 裝置上建置並執行 iOS 應用程式

iOS 應用程式專案是在 Visual Studio 中建立及編輯，但由於授權限制，它必須從 Mac 建置及部署。 Visual Studio 會與 Mac 上所執行的遠端代理程式通訊，以傳輸專案檔，並執行建置、部署和偵錯命令。 安裝並設定 Mac 和 Visual Studio 以進行通訊，才能建置 iOS 應用程式。 如需詳細指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 一旦在 Mac 上執行遠端代理程式，並與 Visual Studio 搭配使用之後，您便可以建置並執行 iOS 應用程式，以確認您的安裝和設定。

若要將 iOS 應用程式部署到 iOS 裝置中，您也必須在 Mac 上設定自動在 Xcode 上簽署。 自動簽署會自動管理應用程式簽署，並建立一個佈建設定檔來簽署應用程式的組建。

### <a name="to-set-up-automatic-signing-on-xcode"></a>若要在 Xcode 上設定自動簽署

1. 如果您還沒有設定，請在 Mac 上安裝 [Xcode](https://developer.apple.com/xcode/downloads/) 10.2.1 版或更新版本。

1. 在 Mac 上開啟 Xcode 應用程式。

1. 建立一個新的**單一檢視應用程式** Xcode 專案。 在專案建立期間填寫必填欄位。 這些值可以是任意的，因為專案僅用於建立稍後用來簽署應用程式組建的佈建設定檔。

1. 將您在 [Apple Developer Program](https://developer.apple.com/programs/) 帳戶中註冊的 Apple ID 加入到 Xcode 中。 您的 Apple ID 會當作簽署應用程式的簽署身分識別使用。 若要在 Xcode 中新增簽署身分識別，請開啟 [Xcode]  功能表，並選擇 [喜好設定]  。 選取 [帳戶]  ，然後按一下 [新增] 按鈕 (+) 來新增您的 Apple ID。 如需詳細指示，請參閱[新增您的 Apple ID 帳戶](https://help.apple.com/xcode/mac/current/#/devaf282080a) \(英文\)。

1. 從 Xcode 專案的 [一般] 設定中，將 [套件組合識別碼]  的值變更為 `com.<NameOfVSProject>`，其中 `<NameOfVSProject>` 是與您所建立的 Visual Studio 方案專案相同的名稱。 例如，如果您在 Visual Studio 上建立一個稱為 `MyOpenGLESApp` 的專案，則將 [套件組合識別碼]  設定為 `com.MyOpenGLESApp`。

   ![Xcode 套件組合識別碼](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. 若要啟用自動簽署，請核取。 自動管理簽署**。

   ![Xcode 自動簽署](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. 選取您當作開發**小組**新增之 Apple ID 的小組名稱。

   ![Xcode 小組](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>若要在 iOS 裝置上建置並執行 iOS 應用程式

1. 在 Mac 上執行遠端代理程式，並確認 Visual Studio 已與遠端代理程式搭配使用。 若要啟動遠端代理程式，請開啟終端機應用程式視窗並輸入 `vcremote`。 如需詳細資訊，請參閱[在 Visual Studio 中設定遠端代理程式](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS)。

   ![執行 vcremote 的 Mac 終端機視窗](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. 將 iOS 裝置連接到 Mac。 當您第一次將裝置連接到電腦時，會出現一個警示，詢問您是否信任存取您裝置的電腦。 讓裝置信任 Mac 電腦。

1. 在 Visual Studio 上，根據您裝置的處理器，從 [方案平台]  下拉式清單中選擇方案平台 (如果尚未選取)。 此範例中為 **ARM64** 處理器。

   ![將方案平台設為 ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. 在 [方案總管] 中，開啟 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [卸載專案]  來卸載專案。

1. 再次開啟已卸載之 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [編輯 project.pbxproj]  來編輯專案檔。 在 `project.pbxproj` 檔案中，尋找 `buildSettings` 屬性，然後使用 Apple Team ID 新增 `DEVELOPMENT_TEAM`。 以下螢幕擷取畫面會針對 Apple Team ID 顯示 `123456ABC` 的範例值。 您可以從 Xcode 找到 Apple Team ID 的值。 移至 [組建設定]  ，並將滑鼠指標停留在您的開發小組名稱上，以顯示工具提示。 工具提示會顯示您的小組識別碼。

   ![設定開發小組](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. 關閉 `project.pbxproj` 檔案，然後開啟已卸載之 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，並選擇 [重新載入專案]  來重新載入專案。

1. 現在，開啟 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [建置]  ，以建置該專案。

   ![建置 iOS 應用程式專案](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   [輸出] 視窗會顯示 iOS 靜態程式庫和 iOS 應用程式的建置流程輸出。 在 Mac 上，執行遠端代理程式的終端機視窗會顯示命令和檔案傳輸活動。

   在 Mac 電腦上，系統可能會提示您允許 Codesign 存取您的 Keychain。 選擇 [允許]  繼續進行。

1. 在工具列上選擇您的 iOS 裝置，以便在連接到 Mac 的裝置上執行應用程式。 如果應用程式未啟動，請確認裝置是否授予已部署的應用程式在裝置上執行的權限。 您可以前往裝置上的 [設定]   > [一般]   > [裝置管理]  來設定此權限。 選取您的開發人員應用程式帳戶、信任您的帳戶，然後驗證應用程式。 再次嘗試從 Visual Studio 執行應用程式。

   ![iOS 裝置上的 iOS 應用程式](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")
   
   在您的應用程式啟動之後，您可以設定中斷點，並使用 Visual Studio 偵錯工具來檢查區域變數、查看呼叫堆疊及監看值。

   ![位於 iOS 應用程式中斷點上的偵錯工具](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. 按 **Shift**+**F5** 停止偵錯。

   產生的 iOS 應用程式和程式庫專案會將 C++ 程式碼放在只實作共用程式碼的靜態程式庫中。 大多數應用程式程式碼會位於 `Application` 專案中。 對這個範本專案中之共用程式庫程式碼的呼叫會在 *GameViewController.m* 檔案中進行。 為了建置您的 iOS 應用程式，Visual Studio 使用 Xcode 平台工具組，該工具組需要與 Mac 上所執行的遠端用戶端進行通訊。

   Visual Studio 會將專案檔和命令傳送到遠端用戶端，以使用 Xcode 建置應用程式。 遠端用戶端會將組建狀態資訊傳回 Visual Studio。 在應用程式順利建置之後，您可以使用 Visual Studio 傳送命令，以執行並偵錯應用程式。 Visual Studio 中的偵錯工具可控制在連接至 Mac 的 iOS 裝置上所執行的應用程式。 Visual Studio 會將 StaticLibrary 專案中的屬性對應至目標 iOS 平台上用來編譯、連結及偵錯的選項。 如需編譯器命令列選項詳細資料，請開啟 MyOpenGLESApp.iOS.StaticLibrary 專案的 [屬性頁]  對話方塊。

## <a name="customize-your-apps"></a>自訂您的應用程式

您可以修改共用的 C++ 程式碼，加入或變更一般常見功能。 您必須在 `MyOpenGLESApp.Android.NativeActivity` 與 `MyOpenGLESApp.iOS.Application` 專案中將對共用程式碼的呼叫變更為相符。 您可以使用前置處理器巨集，來指定通用程式碼中的平台專屬區段。 當您針對 Android 建置時，系統會預先定義前置處理器巨集 `__ANDROID__` 。 當您針對 iOS 建置時，系統會預先定義前置處理器巨集 `__APPLE__` 。

若要查看特定專案平台的 IntelliSense，請在編輯器視窗頂端的巡覽列中，選擇內容切換器下拉式清單中的專案。

![編輯器中的專案內容切換器下拉式清單](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

目前專案所使用之程式碼中的 IntelliSense 問題會以紅色波浪線標示。 其他專案中的問題會以紫色波浪線標示。 Visual Studio 不支援 Java 或 Objective-C 檔案的程式碼顏色標示或 IntelliSense。 不過，您仍然可以修改原始程式檔及變更資源，以設定您的應用程式名稱、圖示和其他實作詳細資料。
