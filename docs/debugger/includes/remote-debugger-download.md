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
ms.openlocfilehash: fec32bf187d629c5fd99ce27eb17a61db39d3873
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839708"
---
遠端裝置或伺服器，您要偵錯，而非在 Visual Studio 電腦，下載並安裝正確版本的遠端工具從下表中的連結。

- 下載最新的遠端工具，您的 Visual Studio 版本。 最新的遠端工具版本與舊版的 Visual Studio 版本中，相容，但是舊版的遠端工具無法與更新版本的 Visual Studio 版本相容。
- 下載與您打算安裝的相同架構與機器的遠端工具。 例如，如果您想要偵錯遠端電腦執行 64 位元作業系統上的 32 位元應用程式，安裝 64 位元遠端工具。

::: moniker range=">=vs-2019"

|版本|連結|注意|
|-|-|-|
|Visual Studio 2019|[遠端工具](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|與所有 Visual Studio 2019 版本相容。 下載符合您裝置的作業系統 (x，x86、 x64、 或 ARM64） 的版本。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載遠端工具的說明。|
|Visual Studio 2017|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|與所有 Visual Studio 2017 版本相容。 下載符合您裝置的作業系統 (x，x86、 x64、 或 ARM64） 的版本。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載遠端工具的說明。|
|Visual Studio 2015|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 遠端工具都是從 My.VisualStudio.com。 如果出現提示，請加入免費[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)程式或使用您的 Visual Studio 訂用帳戶識別碼。 登入。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載遠端工具的說明。|
|Visual Studio 2013|[遠端工具](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|下載 Visual Studio 2013 文件中的頁面|
|Visual Studio 2012|[遠端工具](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|下載 Visual Studio 2012 文件中的頁面|

::: moniker-end

::: moniker range="vs-2017"

|版本|連結|注意|
|-|-|-|
|Visual Studio 2017|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|與所有 Visual Studio 2017 版本相容。 下載符合您裝置的作業系統 (x，x86、 x64、 或 ARM64） 的版本。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載遠端工具的說明。 如需遠端工具的最新版本中，開啟[Visual Studio 2019 doc](../../debugger/remote-debugging.md?view=vs-2019)。|
|Visual Studio 2015|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 遠端工具都是從 My.VisualStudio.com。 如果出現提示，請加入免費[Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/)程式或使用您的 Visual Studio 訂用帳戶識別碼。 登入。 在 Windows 伺服器上，請參閱[解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md)下載遠端工具的說明。|
|Visual Studio 2013|[遠端工具](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|下載 Visual Studio 2013 文件中的頁面|
|Visual Studio 2012|[遠端工具](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|下載 Visual Studio 2012 文件中的頁面|

::: moniker-end

您可以執行遠端偵錯工具複製*msvsmon.exe*遠端電腦，而不是安裝遠端工具。 不過，遠端偵錯工具組態精靈 (*rdbgwiz.exe*) 是使用只有當您安裝遠端工具。 您可能需要使用組態精靈，如果您想要以服務方式執行遠端偵錯工具。 如需詳細資訊，請參閱 < [（選擇性） 設定為服務的遠端偵錯工具](../../debugger/remote-debugging.md#bkmk_configureService)。

>[!NOTE]
>- 若要偵錯 ARM 裝置上的 Windows 10 應用程式，請使用 ARM64，可使用最新版的遠端工具。
>- 若要偵錯在 Windows RT 裝置上的 Windows 10 應用程式，請使用 ARM，僅適用於 Visual Studio 2015 遠端工具下載。
