---
title: 同步處理 XCode 和 Visual Studio 之間的變更 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xamarin
ms.openlocfilehash: 665eafb9a564ffc140e2784665b5f872eaf0eec9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818243"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>同步 XCode 和 Visual Studio 之間的變更
適用於行動裝置開發的 Microsoft Visual C++ 元件，包含可在您的電腦與 Mac 之間同步處理工作的遠端功能。 當您將 Visual Studio 和 Mac 電腦配對之後，Visual Studio 中就會提供適用於 iOS 應用程式專案的新選項，讓您可用來在 XCode 中開啟專案、在 XCode 和 Visual Studio 之間移動程式碼，以及清除暫存的 XCode 專案目錄。

 若要使用 [遠端電腦] 選項，您的專案必須是 iOS 應用程式專案，而且必須將 Visual Studio 與您的 Mac 配對。 如需如何配對 Mac 的必要條件和指示，請參閱[安裝和設定工具以使用 iOS 建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。

## <a name="the-remote-machine-menu"></a>遠端電腦功能表
 在 [方案總管] 中，以滑鼠右鍵按一下 iOS 應用程式專案來顯示快顯功能表。 選取 [遠端電腦] 項目，以顯示可用的遠端選項。

 ![[方案總管] 中的 [遠端電腦] 功能表項目](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 這些命令可讓您在 XCode 中開啟專案、在 Visual Studio 和 XCode 之間移動本機變更或整個專案，以及清除遠端電腦上的暫存檔案。

### <a name="open-in-xcode"></a>在 XCode 中開啟
 若要從 Visual Studio 在 XCode 中開啟專案，在 [遠端電腦] 子功能表上，選擇 [在 XCode 中開啟]，以便在配對的遠端電腦上開啟選取的專案。 vcremote 伺服器可用來在您的 Mac 上開啟 XCode，並瀏覽至您 Mac 上所建立且包含專案複本的暫存目錄。 Visual Studio 會出現一個對話方塊，顯示用於專案的暫存目錄。 遠端電腦上所採取的動作也會顯示在 Visual Studio 的 [輸出] 視窗中。 若要查看它們，您可能需要在 [輸出] 視窗頂端的 [顯示輸出來源] 下拉式清單中，選取 [Visual C++ 遠端電腦]。

 ![[輸出] 視窗會顯示遠端電腦的動作。](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

 在 Mac 上，您可以使用所有的 XCode 工具來編輯您的程式碼和資源、分鏡腳本和動作。 在 Visual Studio 中，您的 iOS 應用程式專案會加上「已在 XCode 中開啟」的註解，以指出可能會在遠端電腦上進行變更。 當您完成編輯之後，可以使用 [從遠端提取] 或 [從遠端累加提取] 命令，將變更複製回您的 Visual Studio 專案。

### <a name="push-to-remote-and-incremental-push-to-remote"></a>推送至遠端和累加推送至遠端
 如果您已在 Visual Studio 中對 iOS 應用程式專案進行變更，可以使用 [推送至遠端] 和 [累加推送至遠端] 命令，將變更的專案檔移至配對的遠端電腦。 [推送至遠端] 命令會將所有專案檔複製到遠端電腦。 [累加推送至遠端] 命令只會將已變更的檔案複製到遠端電腦。 針對只進行小變更的大型專案，累加式命令可以節省時間和頻寬。

 若要將專案檔複製到 Mac，在 Visual Studio 的 [方案總管] 中，以滑鼠右鍵按一下 iOS 應用程式專案，以開啟操作功能表。 選取 [遠端電腦]，然後選擇 [推送至遠端] 或 [累加推送至遠端]，以便將專案檔從 Visual Studio 複製到 Mac。

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>從遠端擷取和從遠端累加提取
 當您在 XCode 中對專案進行任何變更之後，請將所做的變更移回 Visual Studio，以使專案能夠保持同步。

 若要從 Mac 複製專案檔，在 Visual Studio 的 [方案總管] 中，以滑鼠右鍵按一下 iOS 應用程式專案，以開啟操作功能表。 選取 [遠端電腦]，然後選擇 [從遠端擷取] 或 [從遠端累加提取]，以便將專案檔從 Mac 複製到 Visual Studio。

### <a name="clean-remote"></a>清除遠端
 您可以使用 [清除遠端] 命令，來刪除遠端電腦上暫存專案目錄中的檔案。 這會在您的 Mac 上移除目錄的內容，包括任何原始程式檔或組建產品。 使用 [清除遠端] 命令之前，請確定您已經使用 [從遠端擷取] 或 [從遠端累加提取]，將所有變更同步處理回到 Visual Studio。

 若要清除遠端電腦上的暫存專案目錄，在 Visual Studio 的 [方案總管] 中，以滑鼠右鍵按一下 iOS 應用程式專案，以開啟操作功能表。 選取 [遠端電腦]，然後選擇 [清除遠端]，以便從 Mac 移除專案目錄檔案。