---
title: 找 Visual Studio |Microsoft Docs
description: 您可以安裝多個相同版本的 Visual Studio 實例。 瞭解如何使用 COM 查詢 API 來尋找您想要的實例。
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8935af62b16ed6dd6d0d5d61412f347a95f32f23
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616284"
---
# <a name="locate-visual-studio"></a>尋找 Visual Studio

從 Visual Studio 2017 開始，您可以安裝相同版本或甚至版本的多個實例。 當您想要在主要開發電腦上預覽新功能，同時保留先前的安裝時，這會很有説明。 由於這些變更，因此沒有可供您用來尋找實例的單一環境變數或登錄值。 相反地，您可以使用 [COM 查詢 API](/dotnet/api/microsoft.visualstudio.setup.configuration) ，根據與延伸模組相關的準則來尋找實例。

這是一種快速、唯讀的 API，其具有適用于原生和 managed 程式碼的 NuGet 套件。

| 程式碼 | 套件 |
| ---- | --- |
| 原生 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| 受控 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

您可以指定路徑或目前的進程，或列舉所有實例，以找出單一實例。 如需如何找出 Visual Studio 的完整範例，請參閱 [我們的範例](https://github.com/Microsoft/vs-setup-samples) 。

## <a name="tools"></a>工具

若要尋找組建環境、PowerShell 腳本、安裝程式及更多案例中的 Visual Studio 和其他工具，有許多開放原始碼工具可直接使用，或隨您自己的腳本重新發佈。

| 專案 | 描述 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 單一檔案原生可執行檔，用來找出符合準則的實例，例如發行或發行前版本、已安裝的產品，以及已安裝的工作負載。 也支援尋找 Visual Studio 2010 和更新版本，但針對 Visual Studio 2017 和更新版本傳回的資訊較少。 如需範例，請參閱 [wiki](https://github.com/Microsoft/vswhere/wiki) 。 |
| [Vssetup.powershell Cmdlet](https://github.com/Microsoft/vssetup.powershell) | PowerShell Cmdlet 支援2.0 和更新版本，可將豐富的資訊以 _vswhere_ 的相同準則來尋找實例，並探索更多有關實例的屬性。 如需範例，請參閱 [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) 。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 自動尋找 _VSIXInstaller_ 並傳遞命令列，以安裝 **.vsix* 檔案。 這項功能在沒有查詢 Api 直接支援的安裝程式中很有用。 如需範例，請參閱 [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) 。 |

## <a name="see-also"></a>另請參閱

* [Visual Studio 2017 安裝程式的變更](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [使用 DTE 啟動 Visual Studio](launch-visual-studio-dte.md)