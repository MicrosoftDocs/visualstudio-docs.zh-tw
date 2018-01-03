---
title: "安裝跨平台行動裝置開發適用的 Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: d677c74d44f1ddc0b250d6763cef4738cd642832
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Install Visual C++ for Cross-Platform Mobile Development
[Visual C++ for Cross-Platform Mobile Development](http://go.microsoft.com/fwlink/p/?LinkId=536383) 是包含在 Visual Studio 2015 中的可安裝元件。 它包含了跨平台的 Visual Studio 範本，並會安裝跨平台工具和 SDK 以便迅速開始使用，讓您不需要自行尋找、下載與設定。 您可以使用 Visual Studio 中的這些工具來輕鬆建立、編輯、偵錯和測試跨平台專案。 本主題描述如何安裝必要的工具和協力廠商軟體，以使用 Visual Studio 開發跨平台應用程式。 如需元件概觀，請參閱 [Visual C++ 跨平台行動開發](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [需求](#Requirements)   
 [取得工具](#GetTheTools)   
 [安裝工具](#InstallTheTools)   
 [Install tools for iOS](#InstallForiOS)   
 [手動安裝或更新相依項目](#ThirdParty)  
  
##  <a name="Requirements"></a> 需求  
  
-   如需安裝需求，請參閱 [Visual Studio 2015 系統需求](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs)。  
  
    > [!IMPORTANT]
    >  如果您使用 Windows 7 或 Windows Server 2008 R2，便可以為傳統型 Windows 應用程式、Android Native Activity 應用程式和程式庫，以及適用於 iOS 的應用程式和程式碼程式庫開發程式碼，但不適用於 Windows 市集或通用 Windows 應用程式。  
  
 若要建置特定裝置平台的應用程式，有幾個額外的需求：  
  
-   Windows Phone 模擬器與 Microsoft Visual Studio Emulator for Android 需要可執行 Hyper-V 的電腦。 您必須先啟用 Windows 中的 HYPER-V 功能，才能安裝和執行模擬器。 如需詳細資訊，請參閱模擬器的[系統需求](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)。  
  
-   搭配 Android SDK 的 x86 Android 模擬器在可執行 Intel HAXM 驅動程式的電腦上效能最佳。 此驅動程式需要 Intel x64 處理器並支援 VT-x 和執行停用位元。 如需詳細資訊，請參閱 [Intel® 硬體加速執行管理器安裝指示 - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385)。  
  
-   建置 iOS 的程式碼需要 Apple ID、iOS 開發人員計劃帳戶，以及可在 OS X Mavericks 或更新版本中執行 [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) 或更新版本的 Mac 電腦。 如需簡單的安裝步驟，請參閱 [Install tools for iOS](#InstallForiOS)。  
  
##  <a name="GetTheTools"></a> 取得工具  
 適用於跨平台行動裝置開發的 Visual C++ 是隨附於 Visual Studio Community、Professional 及 Enterprise 版本中的可安裝元件。 若要取得 Visual Studio，請移至 [Visual Studio 2015 下載](http://go.microsoft.com/fwlink/p/?linkid=517106)頁面，並下載 Visual Studio 2015 Update 2 或更新版本。  
  
##  <a name="InstallTheTools"></a> 安裝工具  
 Visual Studio 2015 的安裝程式包含安裝 Visual C++ for Cross-Platform Mobile Development 的選項。 這會安裝必要的 C++ 語言工具、適用於 Visual Studio 的範本和元件、Android 組建和偵錯所需的 GCC 和 Clang 工具組元件，以及與 Mac 通訊的 iOS 開發元件。 它也會安裝支援 iOS 和 Android 應用程式開發所需的所有協力廠商工具和軟體開發套件。 大多數協力廠商工具是 Android 平台支援所需的開放原始碼軟體。  
  
-   建置以 Android 平台為目標的 C++ 程式碼需要 Android 原生開發套件 (NDK)。  
  
-   Android 建置流程需要 Android SDK、Apache Ant 及 Java SE Development Kit。  
  
-   Microsoft Visual Studio Emulator for Android 是一款選用的高效能模擬器，非常適合進行程式碼測試與偵錯。  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>若要安裝 Visual C++ for Cross-Platform Mobile Development 和協力廠商工具  
  
1.  請於 [取得工具](#GetTheTools)中的連結下載 Visual Studio 2015 安裝程式，並執行。 若要安裝選用元件，請選擇 [自訂]  做為安裝類型。 選擇 [下一步]  ，選取要安裝的選用元件。  
  
2.  在 [選取功能] 中，展開 [跨平台行動開發]  ，然後核取 [Visual C++ 行動開發] 。  
  
     ![選取 Visual C++ 行動開發](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")  
  
     根據預設，當您選取 [Visual C++ 行動開發] 時，會設定 [程式語言] 選項以安裝 [Visual C++]，並設定 [常用工具及軟體開發套件] 選項以安裝協力廠商的必要元件。 您可以視需要選擇其他元件。 預設也會選取 [Android 版 Microsoft Visual Studio 模擬器]。 已安裝的元件在清單中會顯示為非使用中。  
  
     若要建置通用 Windows 應用程式，並在您的 Android 和 iOS 專案之間共用程式碼，在 [選取功能] 中，展開 [Windows 及 Web 程式開發]，然後核取 [通用 Windows 應用程式開發工具]。 如果您不打算建置通用 Windows 應用程式，則可略過此選項。  
  
     選擇 [下一步]  繼續進行。  
  
3.  協力廠商元件會有自己的授權條款。 您可以選擇每個元件旁的 [授權條款]  連結，以檢視授權條款。 選擇 [安裝] 來新增元件，並安裝 Visual Studio 和適用於跨平台行動裝置開發的 Visual C++。  
  
4.  安裝完成時，關閉安裝程式，然後重新啟動電腦。 適用於協力廠商元件的部分安裝動作要在重新啟動電腦之後才會生效。  
  
    > [!IMPORTANT]
    >  您必須重新啟動，確定一切都已正確安裝。  
  
     如果無法安裝 Android 版 Microsoft Visual Studio 模擬器元件，則您的電腦可能並未啟用 HYPER-V。 使用 [開啟或關閉 Windows 功能] 控制台應用程式來啟用 HYPER-V，然後再次執行 Visual Studio 安裝程式。  
  
    > [!NOTE]
    >  如果您的電腦或 Windows 版本不支援 HYPER-V，您就無法使用Android 版 Microsoft Visual Studio 模擬器元件。 Windows 的 Home Edition 不包含 HYPER-V 支援。  
  
5.  開啟 Visual Studio。 如果這是您第一次執行 Visual Studio，可能需要一些時間來設定和登入。 當 Visual Studio 就緒時，請在 [工具]  功能表中依序選取 [擴充功能和更新] 、[更新] 。 如果有適用於 Visual C++ for Cross-Platform Mobile Development 或 Microsoft Visual Studio Emulator for Android 的 Visual Studio 更新，請加以安裝。  
  
##  <a name="InstallForiOS"></a> Install tools for iOS  
 您可以使用 Visual C++ for Cross-Platform Mobile Development 編輯、偵錯 iOS 程式碼並將其部署至 iOS 模擬器或 iOS 裝置，但由於授權限制，必須在 Mac 上遠端建置程式碼。 若要使用 Visual Studio 建置並執行 iOS 應用程式，您必須在 Mac 上安裝及設定遠端代理程式。 如需詳細的安裝指示、必要條件及組態選項，請參閱 [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 如果您不是針對  iOS 進行建置，可以略過此步驟。  
  
##  <a name="ThirdParty"></a> 手動安裝或更新相依項目  
 如果您在安裝 Visual C++ Mobile Development 選項時，決定不要安裝一或多個使用 Visual Studio 安裝程式的協力廠商相依項目，可使用 [Install the tools](#InstallTheTools)中的步驟於稍後安裝。 您也可以獨立於 Visual Studio 安裝或更新這些項目。  
  
> [!CAUTION]
>  您可以依任何順序安裝相依項目，除了 Java 之外。 您必須先安裝及設定 JDK，再安裝 Android SDK。  
  
 請閱讀下列資訊並使用這些連結，以手動安裝相依項目。  
  
-   [Java SE 開發套件](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
     依預設，安裝程式會將 Java 工具放在 C:\Program Files (x86)\Java。  
  
-   [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
     在安裝期間，請依照建議更新 API。 確定至少已安裝 Android 5.0 Lollipop (API 層級 21) 的 SDK。 依預設，安裝程式會將 Android SDK 放在 C:\Program Files (x86)\Android\android-sdk。  
  
     您可以在 Android SDK 目錄重新執行 SDK Manager 應用程式來更新 SDK，並安裝選擇性工具和其他 API 層級。 除非您使用 [以系統管理員身分執行]  執行 SDK Manager 應用程式，否則可能無法安裝更新。 如果您有建置 Android 應用程式的問題，請檢查 SDK Manager 以確認已安裝的 SDK 是否有更新。  
  
     若要使用 Android SDK 隨附的一些 Android 模擬器，您必須安裝選擇性的 Intel HAXM 驅動程式。 您可能必須從 Windows 移除 Hyper-V 功能，以便順利安裝 Intel HAXM 驅動程式。 您必須還原 Hyper-V 功能，以使用 Windows Phone 模擬器和 Microsoft Visual Studio Emulator for Android。  
  
-   [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
     根據預設，安裝程式會將 Android NDK 放在 C:\ProgramData\Microsoft\AndroidNDK。 您可以重新下載並安裝 Android NDK，以更新 NDK 安裝。  
  
-   [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
     依預設，安裝程式會將 Apache Ant 放在 C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps 中。  
  
-   [Android 版 Microsoft Visual Studio 模擬器](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
     您可以從 Visual Studio 組件庫安裝和更新 Microsoft Visual Studio Emulator for Android。  
  
 在大多數情況中，Visual Studio 皆可偵測您已安裝之協力廠商軟體的組態，並保留內部環境變數中的安裝路徑。 您可以在 Visual Studio IDE 中覆寫這些跨平台開發工具的預設路徑。  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>若要設定協力廠商工具的路徑  
  
1.  在 Visual Studio 功能表列上，依序選取 [工具] 、[選項] 。  
  
2.  展開 [選項]  對話方塊中的 [跨平台] 、[C++] ，並選取 [Android] 。  
  
     ![Android 工具路徑選項](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")  
  
3.  若要變更工具所使用的路徑，請核取路徑旁的核取方塊，並在文字方塊中編輯資料夾路徑。 您也可以使用瀏覽按鈕 (**...**)，開啟 [選取位置]  對話方塊並選擇資料夾。  
  
4.  選擇 [確定]  ，儲存自訂工具資料夾的位置。  
  
## <a name="see-also"></a>請參閱  
 [安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ 跨平台行動開發](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)