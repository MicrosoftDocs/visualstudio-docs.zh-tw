---
title: 尋找 Visual Studio |Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9d74c0a899139046cab1d73b59086e4ab9e2276
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955129"
---
# <a name="locate-visual-studio"></a>尋找 Visual Studio

從 Visual Studio 2017 開始，您可以安裝相同版本或甚至是版本的多個執行個體。 當您想要預覽的主要開發電腦上的新功能，同時保留先前的安裝，這是很有幫助。 由於這些變更，沒有單一的環境變數或登錄值可用來找出執行個體。 相反地，您可以使用[COM 查詢 API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx)尋找與您的延伸模組相關的準則為基礎的執行個體。

這是快速、 唯讀 API，使用適用於原生和 managed 程式碼的 NuGet 套件。

| 程式碼 | 封裝 |
| ---- | --- |
| 原生 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Managed | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

您可以找出指定的路徑或目前的處理序的單一執行個體，或列舉所有的執行個體。 請參閱[我們的範例](https://github.com/Microsoft/vs-setup-samples)如需如何找出 Visual Studio 的完整範例。

## <a name="tools"></a>工具

若要尋找 Visual Studio 和其他工具，在建置環境、 PowerShell 指令碼、 安裝程式，以及更多的案例中，有幾個開放原始碼工具，您可以直接使用或轉散發，以及您自己的指令碼。

| 專案 | 描述 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 單一檔案原生可執行檔來找出符合準則，例如版本或發行前版本，已安裝哪些產品，以及哪些工作負載會安裝的執行個體。 也支援尋找 Visual Studio 2010 及更新版本中，但較少的資訊傳回，Visual Studio 2017 及更新版本。 請參閱[wiki](https://github.com/Microsoft/vswhere/wiki)的範例。 |
| [VSSetup cmdlet](https://github.com/Microsoft/vssetup.powershell) | PowerShell cmdlet 支援 2.0 及更新版本中，會傳回可用來尋找相同的條件為基礎的執行個體做為物件豐富的資訊_vswhere_和用來探索更多執行個體相關的屬性。 請參閱[wiki](https://github.com/Microsoft/vssetup.powershell/wiki)的範例。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 會自動找出_VSIXInstaller_並將透過命令列傳遞至安裝 **.vsix*檔案。 這項功能可用於不需要直接查詢 Api 支援的安裝程式。 請參閱[wiki](https://github.com/Microsoft/vsixbootstrapper/wiki)的範例。 |

## <a name="see-also"></a>另請參閱

* [Visual Studio 2017 安裝程式的變更](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup/)
