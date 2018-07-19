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
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809236"
---
1.  裝置或伺服器機器，您要偵錯 （而非執行 Visual Studio 的電腦），取得正確的遠端工具版本。

    |版本|連結|注意|
    |-|-|-|
    |Visual Studio 2017 （最新版）|[遠端工具](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|一律下載符合您裝置的作業系統 (x，x86、 x64、 或 ARM64） 的版本。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging.md#unblock_msvsmon)下載的遠端工具的說明。|
    |Visual Studio 2017 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|舊版的 Visual Studio 2017 遠端工具都是從 My.VisualStudio.com。 出現提示時，加入免費的 Visual Studio Dev Essentials 群組或使用 Visual Studio 訂用帳戶登入識別碼。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging.md#unblock_msvsmon)下載的遠端工具的說明。|
    |Visual Studio 2015 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|出現提示時，加入免費的 Visual Studio Dev Essentials 群組或使用 Visual Studio 訂用帳戶登入識別碼。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging.md#unblock_msvsmon)下載的遠端工具的說明。|
    |Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2013 文件中的頁面|
    |Visual Studio 2012|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2012 文件中的頁面|

2.  在下載頁面上，選擇符合您作業系統 （x86、 x64、 ARM、 或 ARM64） 的工具版本，並下載遠端工具。

    > [!IMPORTANT]
    >  我們建議您安裝最新的遠端工具版本符合您的 Visual Studio 版本。 不建議使用不相符的版本。 此外，您必須安裝具有相同的架構做為您想要將它安裝所在的作業系統的遠端工具。 換句話說，如果您想要偵錯遠端電腦執行 64 位元作業系統上的 32 位元應用程式，您就必須在遠端電腦上安裝 64 位元版本的遠端工具。
    >
    >  Windows 10 上偵錯 ARM 裝置上，選擇 ARM64 下載最新版本的遠端工具。  對於 Windows RT 的裝置，選擇 ARM 版本，才可在 Visual Studio 2015 的 RTW 下載中。

3.  當您完成下載可執行檔時，請移至下一節，並遵循安裝指示。

如果您嘗試複製到遠端電腦的遠端偵錯工具 (msvsmon.exe) 並加以執行，請注意，**遠端偵錯工具組態精靈**(**rdbgwiz.exe**) 才會安裝您所下載工具。 您可能需要使用精靈來建立組態之後，特別是如果您想要以服務方式執行遠端偵錯工具。 如需詳細資訊，請參閱 < [（選擇性） 設定為服務的遠端偵錯工具](../../debugger/remote-debugging.md#bkmk_configureService)。
