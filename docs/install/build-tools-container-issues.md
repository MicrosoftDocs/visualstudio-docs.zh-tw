---
title: "容器的已知問題 | Microsoft Docs"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 75825d368d0098c466c44a23fa18ac1af7b06e64
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="known-issues-for-containers"></a>容器的已知問題

將 Visual Studio 安裝到 Docker 容器時有幾個問題。

## <a name="windows-container"></a>Windows 容器

當您將 Visual Studio Build Tools 2017 安裝到 Windows 容器時，會發生下列已知問題。

* 您無法將 Visual Studio 安裝到以映像 microsoft/windowsservercore:10.0.14393.1593 為基礎的容器。 以更舊或更新的 Windows 版本標記的映像應該會運作正常。
* 您無法安裝早於 10.0.14393 的 Windows SDK 版本。 某些套件無法安裝，且相依於這些套件的工作負載將無法運作。
* 建立映像時，您必須傳遞 `-m 2GB` (或以上)。 某些工作負載在安裝時，需要比預設 1 GB 更多的記憶體。
* 您必須設定 Docker 使用大於預設 20 GB 的磁碟。
* 您必須在命令列上傳遞 `--norestart`。 在撰寫本文時，嘗試從容器內重新啟動 Windows 容器會傳回 `ERROR_TOO_MANY_OPEN_FILES` 給主機。

## <a name="build-tools-container"></a>建置工具容器

當您使用建置工具容器時，可能會發生下列已知問題。 若要查看問題是否已獲得修正，或是否有其他已知問題，請瀏覽 https://developercommunity.visualstudio.com。

* 在[某些情況](https://github.com/Microsoft/vstest/issues/940)下，IntelliTrace 在容器內可能無法運作。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面，以取得疑難排解祕訣。 同樣地，您可以透過 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具向我們報告產品問題，或者在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享建議。 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。 您也可以透過我們在 [Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動 (需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>請參閱

* [將建置工具安裝至容器](build-tools-container.md)
* [容器的進階範例](advanced-build-tools-container.md)
