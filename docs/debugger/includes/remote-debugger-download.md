---
title: 遠端偵錯程式下載
description: 下載遠端偵錯程式的連結
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 86bc2a1b73b492dc5f8d9977f05c3b2ba0dde6dc
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91376657"
---
在您想要進行偵錯工具的遠端裝置或伺服器上（而不是 Visual Studio 電腦），從下表的連結下載並安裝正確的遠端工具版本。

- 下載適用于您 Visual Studio 版本的最新遠端工具。 最新的遠端工具版本與先前的 Visual Studio 版本相容，但較舊的遠端工具版本與稍後的 Visual Studio 版本不相容。  (例如，如果您使用 Visual Studio 2017，請下載適用于 Visual Studio 2017 的最新遠端工具更新。 在此案例中，請勿下載 Visual Studio 2019 的遠端工具。 ) 
- 下載遠端工具，其架構與您要安裝它們的電腦相同。 例如，如果您想要在執行64位作業系統的遠端電腦上進行32位應用程式的偵錯工具，請安裝64位的遠端工具。

::: moniker range=">=vs-2019"

|版本|連結|附註|
|-|-|-|
|Visual Studio 2019|[遠端工具](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|與所有 Visual Studio 2019 版本相容。 下載符合您裝置作業系統 (x86、x64 或 ARM64) 的版本。 在 Windows Server 上，請參閱 [解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md) ，以取得下載遠端工具的協助。|
|Visual Studio 2017|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|與所有 Visual Studio 2017 版本相容。 下載符合您裝置作業系統 (x86、x64 或 ARM64) 的版本。 在 Windows Server 上，請參閱 [解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md) ，以取得下載遠端工具的協助。|
|Visual Studio 2015|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|您可以從 My.VisualStudio.com 取得 Visual Studio 2015 的遠端工具。 如果出現提示，請加入免費的 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 程式，或使用您 Visual Studio 的訂用帳戶識別碼登入。 在 Windows Server 上，請參閱 [解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md) ，以取得下載遠端工具的協助。|
|Visual Studio 2013|[遠端工具](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 檔中的下載頁面|
|Visual Studio 2012|[遠端工具](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 檔中的下載頁面|

::: moniker-end

::: moniker range="vs-2017"

|版本|連結|附註|
|-|-|-|
|Visual Studio 2017|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|與所有 Visual Studio 2017 版本相容。 下載符合您裝置作業系統 (x86、x64 或 ARM64) 的版本。 在 Windows Server 上，請參閱 [解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md) ，以取得下載遠端工具的協助。 如需最新版本的遠端工具，請開啟 [Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019&preserve-view=true)檔。|
|Visual Studio 2015|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|您可以從 My.VisualStudio.com 取得 Visual Studio 2015 的遠端工具。 如果出現提示，請加入免費的 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 程式，或使用您 Visual Studio 的訂用帳戶識別碼登入。 在 Windows Server 上，請參閱 [解除封鎖檔案下載](../../debugger/remote-debugging-unblock-file-download.md) ，以取得下載遠端工具的協助。|
|Visual Studio 2013|[遠端工具](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 檔中的下載頁面|
|Visual Studio 2012|[遠端工具](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 檔中的下載頁面|

::: moniker-end

您可以將 *msvsmon.exe* 複製到遠端電腦，而不是安裝遠端工具，藉以執行遠端偵錯程式。 不過，只有當您安裝遠端工具時，才可以使用 [遠端偵錯程式設定] (*rdbgwiz.exe*) 。 如果您想要以服務的形式執行遠端偵錯程式，您可能需要使用 wizard 進行設定。 如需詳細資訊，請參閱 [ (選擇性) 將遠端偵錯程式設定為服務](../../debugger/remote-debugging.md#bkmk_configureService)。

>[!NOTE]
>- 若要在 ARM 裝置上進行 Windows 10 應用程式的偵錯工具，請使用最新版本的遠端工具所提供的 ARM64。
>- 若要在 Windows RT 裝置上進行 Windows 10 應用程式的偵錯工具，請使用 ARM，這僅適用于 Visual Studio 2015 遠端工具下載。
