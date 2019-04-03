---
title: 解除安裝 Visual Studio for Mac
description: 解除安裝 Visual Studio for Mac 和相關工具的指示。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 2a0b1e14dd822c159484dcaed052a13a35d43939
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568600"
---
# <a name="uninstalling-visual-studio-for-mac"></a>解除安裝 Visual Studio for Mac

有許多 Xamarin 產品可啟用跨平台應用程式開發，包含 Visual Studio for Mac 這類獨立應用程式。

您可以使用本指南來個別解除安裝每項產品，方法是巡覽至相關章節，或使用[解除安裝指令碼](#uninstall-script)一節中提供的指令碼，以解除安裝所有項目。

如果您先前已在電腦上安裝 Xamarin Studio，則除了下列步驟之外，還可能需要遵循 [Xamarin 解除安裝](/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac)指南中的指示。

## <a name="uninstall-script"></a>解除安裝指令碼

有兩個指令碼可用來解除安裝您電腦的 Visual Studio for Mac 和所有元件：

- [Visual Studio 和 Xamarin 指令碼](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core 指令碼](#net-core-script)

下列各節提供有關下載和使用指令碼的資訊。

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Visual Studio for Mac 和 Xamarin 指令碼

使用[解除安裝指令碼](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)即可透過一個步驟將 Visual Studio 和 Xamarin 元件解除安裝。

此解除安裝指令碼包含您將在文章中發現的大部分命令。 指令碼中有三個主要省略項目，並且因可能的外部相依性而未包含。 若要移除這種情況，請跳到以下相關小節，然後手動移除它們：

- **[解除安裝 Mono](#uninstall-mono-sdk-mdk)**
- **[解除安裝 Android AVD](#uninstall-android-avd)**
- **[解除安裝 Android SDK 和 Java SDK](#uninstall-android-sdk-and-java-sdk)**

若要執行指令碼，請執行下列步驟：

1. 以滑鼠右鍵按一下指令碼，然後選取 [另存新檔] 將檔案儲存在您的 Mac 上。
2. 開啟 [終端機]，並將工作目錄變更為已下載指令碼的位置：

    ```bash
    cd /location/of/file
    ```
3. 將指令碼設為可執行，並使用 **sudo** 執行它：

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```
4. 最後，刪除解除安裝指令碼。

### <a name="net-core-script"></a>.NET Core 指令碼

.NET Core 的解除安裝指令碼位於[存放庫](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)中

若要執行指令碼，請執行下列步驟：

1. 以滑鼠右鍵按一下指令碼，然後選取 [另存新檔] 將檔案儲存在您的 Mac 上。
2. 開啟 [終端機]，並將工作目錄變更為已下載指令碼的位置：

    ```bash
    cd /location/of/file
    ```
3. 將指令碼設為可執行，並使用 **sudo** 執行它：

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```
4. 最後，刪除 .NET Core 解除安裝指令碼。

## <a name="uninstall-visual-studio-for-mac"></a>解除安裝 Visual Studio for Mac

從 Mac 解除安裝 Visual Studio 的第一個步驟是找出 **/Applications** 目錄中的 **Visual Studio.app**，並將它拖曳至 [資源回收筒]。 或者以滑鼠右鍵按一下並選取 [移至垃圾桶]，如下圖所示：

![將 Visual Studio 應用程式移至垃圾桶](media/uninstall-image1.png)

刪除此應用程式套件組合會移除 Visual Studio for Mac，即使檔案系統上仍然有其他 Xamarin 相關檔案也是一樣。

若要移除 Visual Studio for Mac 的所有追蹤，請在終端機中執行下列命令：

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

您可能也想要移除下列包含各種 Xamarin 檔案和資料夾的目錄。 不過，這麼做之前，您應該知道此目錄包含 Android 簽署金鑰。 如需詳細資訊，請參閱**[解除安裝 Android SDK 和 Java SDK](#uninstall-android-sdk-and-java-sdk)** 一節：

```bash
rm -rf ~/Library/Developer/Xamarin
```


## <a name="uninstall-mono-sdk-mdk"></a>解除安裝 Mono SDK (MDK)

Mono 是 Microsoft .NET Framework 的開放原始碼實作，並供所有 Xamarin 產品 (Xamarin.iOS、Xamarin.Android 和 Xamarin.Mac) 使用，以允許使用 C# 開發這些平台。

> [!WARNING]
> Visual Studio for Mac 外部有其他應用程式也使用 Mono，例如 Unity。
> 請先確認沒有與 Mono 的其他相依性，再將它解除安裝。

若要從電腦中移除 Mono Framework，請在終端機中執行下列命令：

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>解除安裝 Xamarin.Android

安裝和使用 Xamarin.Android 需要許多項目，例如 Android SDK 和 Java SDK。

您可以使用下列命令移除 Xamarin.Android：

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>解除安裝 Android SDK 和 Java SDK

需要有 Android SDK，才能開發 Android 應用程式。 若要完全移除 Android SDK 的所有部分，請在 **~/Library/Developer/Xamarin/** 找出檔案，並將它移至 [垃圾]。

> [!WARNING]
> 您應該知道 Visual Studio for Mac 所產生的 Android 簽署金鑰位於 `~/Library/Developer/Xamarin/Keystore`。 請務必適當地備份這些金鑰或避免移除此目錄 (如果您想要保留金鑰儲存區)。

不需要解除安裝 Java SDK (JDK)，因為它已預先封裝為 Mac OS X/macOS 的一部分。

### <a name="uninstall-android-avd"></a>解除安裝 Android AVD

> [!WARNING]
> Visual Studio for Mac 外部有其他應用程式也使用 Android AVD 以及這些額外的 Android 元件，例如 Android Studio。移除這個目錄可能會造成專案在 Android Studio 內中斷。

若要移除任何 Android AVD 和額外 Android 元件，請使用下列命令：

```bash
rm -rf ~/.android
```

若只要移除 Android AVD，請使用下列命令：

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>解除安裝 Xamarin.iOS

Xamarin.iOS 允許搭配使用 C# 或 F# 與 Visual Studio for Mac 來進行 iOS 應用程式開發。

在終端機使用下列命令，從檔案系統移除所有 Xamarin.iOS 檔案：

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>解除安裝 Xamarin.Mac

可以在您的 Mac 中分別使用下列兩個命令來根除產品及授權，以從電腦移除 Xamarin.Mac：

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>解除安裝 Workbooks 和 Inspector

從 1.2.2 開始，執行下列命令，即可從終端機解除安裝 Xamarin Workbooks 和 Inspector：

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

若為舊版本，您可能需要手動移除下列成品：

* 刪除 `"/Applications/Xamarin Workbooks.app"` 上的 Workbooks 應用程式
* 刪除 `"Applications/Xamarin Inspector.app"` 上的 Inspector 應用程式
* 刪除增益集：`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` 和 `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* 刪除這裡的 Inspector 和支援檔：`/Library/Frameworks/Xamarin.Interactive.framework` 和 `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>解除安裝 Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>解除安裝 Visual Studio 安裝程式

使用下列命令，移除 Xamarin Universal Installer 的所有追蹤：

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>另請參閱

- [解除安裝 Visual Studio (Windows 上)](/visualstudio/install/uninstall-visual-studio)