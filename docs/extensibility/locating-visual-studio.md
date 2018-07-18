---
title: 尋找 Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 08/21/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed6125c69b9068ebfb3d776ccbefaf88043f83a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138609"
---
# <a name="locating-visual-studio"></a>尋找 Visual Studio

從 Visual Studio 2017 開始，您可以安裝相同版本或甚至版本的多個執行個體。 當您想要預覽您的主要開發電腦上的新功能，同時保留先前的安裝時，這是很有幫助。 這些變更，因為沒有單一的環境變數或登錄值可用來找出執行個體。 相反地，您可以使用[COM 查詢 API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx)尋找適用於您的擴充功能的準則為基礎的執行個體。

這是快速且唯讀的 API 以 NuGet 套件適用於原生和 managed 程式碼。

| 程式碼 | Package |
| ---- | --- |
| 原生 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Managed | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

您可以找出指定之路徑或目前的處理序的單一執行個體，或列舉所有的執行個體。 請參閱[我們的範例](https://github.com/Microsoft/vs-setup-samples)如需如何尋找 Visual Studio 的完整範例。

## <a name="tools"></a>工具

若要在建置環境、 PowerShell 指令碼，安裝程式，以及更多的案例中，尋找 Visual Studio 和其他工具，我們有許多開放原始碼工具，您可以直接使用，或是您自己的指令碼以及轉散發。

| 專案 | 描述 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 單一檔案原生可執行檔以找出符合準則，例如版本或發行前版本，已安裝哪些產品，而且其工作負載所安裝的執行個體。 也支援尋找 Visual Studio 2010 及更新版本中，雖然較少會傳回資訊，Visual Studio 2017 及更新版本。 請參閱[wiki](https://github.com/Microsoft/vswhere/wiki)範例。 |
| [VSSetup cmdlet](https://github.com/Microsoft/vssetup.powershell) | PowerShell 指令程式支援 2.0 及更新版本中，傳回可用來尋找做為相同的準則為基礎的執行個體做為物件豐富的資訊_vswhere_以及探索更多執行個體的相關屬性。 請參閱[wiki](https://github.com/Microsoft/vssetup.powershell/wiki)範例。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 會自動找到_VSIXInstaller_並將透過命令列傳遞至安裝 _*.vsix_檔案。 這可以是不需要直接查詢 Api 支援的安裝中很有用。 請參閱[wiki](https://github.com/Microsoft/vsixbootstrapper/wiki)範例。 |

## <a name="see-also"></a>另請參閱

* [Visual Studio 2017 安裝程式的變更](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
