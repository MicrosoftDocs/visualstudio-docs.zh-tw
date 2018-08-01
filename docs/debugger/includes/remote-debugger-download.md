---
title: 遠端偵錯工具下載
description: 遠端偵錯工具的下載連結
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 491b01d87e4f1a9980143e9ffcc501b3cda7c922
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39189468"
---
1.  裝置或伺服器機器，您要偵錯 （而非執行 Visual Studio 的電腦），取得正確的遠端工具版本。

    |版本|連結|注意|
    |-|-|-|
    |Visual Studio 2017 （最新版）|[遠端工具](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|最新版的遠端工具適用於所有的 Visual Studio 2017 版本。 一律下載符合您裝置的作業系統 (x，x86、 x64、 或 ARM64） 的版本。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載的遠端工具的說明。|
    |Visual Studio 2015|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 遠端工具都是從 My.VisualStudio.com。 如果出現提示，請加入免費[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)程式或使用您的 Visual Studio 訂用帳戶識別碼。 登入。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載的遠端工具的說明。|
    |Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2013 文件中的頁面|
    |Visual Studio 2012|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2012 文件中的頁面|

2.  在下載頁面上，選擇符合您作業系統 （x86、 x64、 ARM、 或 ARM64） 的工具版本，並下載遠端工具。

    > [!IMPORTANT]
    >  我們建議您為發行的 Visual Studio 安裝遠端工具的最新版本。 最新版本 (例如，15.8) 適用於較早的版本 (例如，15.0);不過，較早版本不相容於更新的版本。 此外，您必須安裝具有相同的架構做為您想要將它安裝所在的作業系統的遠端工具。 換句話說，如果您想要偵錯遠端電腦執行 64 位元作業系統上的 32 位元應用程式，您就必須在遠端電腦上安裝 64 位元版本的遠端工具。
    >
    >  Windows 10 上偵錯 ARM 裝置上，選擇 ARM64 下載最新版本的遠端工具。  對於 Windows RT 的裝置，選擇 ARM 版本，才可在 Visual Studio 2015 的 RTW 下載中。

3.  當您完成下載可執行檔時，請移至下一節，並遵循安裝指示。

如果您嘗試複製到遠端電腦的遠端偵錯工具 (msvsmon.exe) 並加以執行，請注意，**遠端偵錯工具組態精靈**(**rdbgwiz.exe**) 才會安裝您所下載工具。 您可能需要使用精靈來建立組態之後，特別是如果您想要以服務方式執行遠端偵錯工具。 如需詳細資訊，請參閱 < [（選擇性） 設定為服務的遠端偵錯工具](../../debugger/remote-debugging.md#bkmk_configureService)。
