---
title: 在 Azure 虛擬機器上使用 Visual Studio
titleSuffix: ''
description: 了解如何在 Azure 虛擬機器上使用 Visual Studio
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 41247c13e8b35fd6e6cd26ac0ad0ea82f742fbb0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306692"
---
# <a name="visual-studio-images-on-azure"></a>Azure 上的 Visual Studio 映像

在預先設定的 Azure 虛擬機器 (VM) 中使用 Visual Studio，是從零開始到建立已啟動並執行中之開發環境的快速簡單方式。 [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure) 中提供具有各種不同 Visual Studio 設定的系統映像。

不熟悉 Azure 嗎？ [建立 Azure 免費帳戶](https://azure.microsoft.com/free)。

## <a name="what-configurations-and-versions-are-available"></a>有哪些設定和版本可用？

在 Azure Marketplace 中，您可以找到適用於最新主要版本的映像：Visual Studio 2019、Visual Studio 2017 和 Visual Studio 2015。  針對每個已發行的主要版本，您會看到原始發行至 Web (RTW) 版本和最新更新版本。  每個版本都提供 Visual Studio Enterprise 和 Visual Studio Community 版本。  這些映像會每個月至少更新一次，以納入最新的 Visual Studio 和 Windows 更新。  雖然映像的名稱會維持不變，但每個映像的描述會納入已安裝的產品版本和映像的「生效」日期。

| 發行版本                                                                                                                                                | 版本              | 產品版本       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019：最新的 (16.8 版) ](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise、Community | 版本16.8。0        |
| [Visual Studio 2019：RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Enterprise            | 版本16.0.20       |
| [Visual Studio 2017：最新 (版本 15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise、Community | 版本15.9.29       |
| [Visual Studio 2017：RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise、Community | 版本 15.0.28       |
| [Visual Studio 2015：最新 (更新 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise、Community | 14.0.25431.01 版 |

> [!NOTE]
> 根據 Microsoft 服務原則，Visual Studio 2015 的原始發行 (RTW) 版本服務期已滿。 Visual Studio 2015 Update 3 是為 Visual Studio 2015 產品線提供的唯一留存版本。

如需詳細資訊，請參閱 [Visual Studio 服務原則](/visualstudio/productinfo/vs-servicing-vs)。

## <a name="what-features-are-installed"></a>安裝的功能有哪些？

每個映像都包含該 Visual Studio 版本的建議功能集。 一般而言，安裝會包括：

* 所有可用的工作負載 (包括每個工作負載的建議選用元件)
* .NET 4.6.2 和 .NET 4.7 SDK、目標套件，以及開發人員工具
* Visual F#
* Visual Studio 的 GitHub 擴充功能
* LINQ to SQL 工具

我們使用下列命令列來在建置映像時安裝 Visual Studio：

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

如果映像並未包含您所需的 Visual Studio 功能，請透過頁面右上角的意見反應工具來提供意見反應。

## <a name="what-size-vm-should-i-choose"></a>應該選擇哪個大小的 VM？

Azure 提供各種不同的虛擬機器大小。 由於 Visual Studio 是一個強大、多執行緒的應用程式，因此您會想要一個至少包含兩個處理器和 7 GB 記憶體的 VM 大小。 以下是 Visual Studio 映像的建議 VM 大小：

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

如需有關最新機器大小的詳細資訊，請參閱 [Azure 中 Windows 虛擬機器的大小](/azure/virtual-machines/windows/sizes) \(機器翻譯\)。

使用 Azure 時，您可以藉由調整 VM 大小來重新平衡您的初始選擇。 您可以佈建大小較適當的新 VM，或調整現有 VM 的大小以配合不同的基礎硬體。 如需詳細資訊，請參閱[調整 Windows VM 大小](/azure/virtual-machines/windows/resize-vm)。

## <a name="after-the-vm-is-running-whats-next"></a>在 VM 執行之後，接下來呢？

Visual Studio 會依循 Azure 中的「自備授權」模型。 如同專用硬體上的安裝，前幾個步驟之一，就是為您的 Visual Studio 安裝取得授權。 若要將 Visual Studio 解除鎖定，請執行下列任何一項作業：

* 使用與 Visual Studio 訂用帳戶相關聯的 Microsoft 帳戶進行登入
* 使用最初購買所隨附的產品金鑰將 Visual Studio 解除鎖定

如需詳細資訊，請參閱[登入 Visual Studio](../ide/signing-in-to-visual-studio.md) 和[如何解除鎖定 Visual Studio](../ide/how-to-unlock-visual-studio.md)。

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>如何儲存開發 VM 以供日後或小組使用？

開發環境的範圍很大，而建置出較複雜環境有一些相關的實際成本。 不論您的環境組態為何，您都可以將已設定的 VM 儲存或擷取成「基底映像」，以供日後使用或供其他小組成員使用。 然後，在啟動新 VM 時，從基底映像佈建它，而不是從 Azure Marketplace 映像。

快速摘要：使用系統準備工具 (Sysprep) 並關閉執行中的 VM，然後透過 Azure 入口網站的 UI 擷取 VM 作為映像 (圖 1)。 Azure 會將包含該映像的 `.vhd` 檔案儲存在您選擇的儲存體帳戶中。 然後，新的映像就會在您訂用帳戶的資源清單中顯示為映像資源。

![透過 Azure 入口網站的 UI 擷取映像](media/capture-vm.png)

*(圖 1) 透過 Azure 入口網站的 UI 擷取映像。*

如需詳細資訊，請參閱[在 Azure 中建立一般化 VM 的受控映像](/azure/virtual-machines/windows/capture-image-resource)。

> [!IMPORTANT]
> 請別忘了使用 Sysprep 來準備 VM。 如果您遺漏該步驟，Azure 將無法從映像佈建 VM。

> [!NOTE]
> 您仍會產生一些儲存映像的成本，但與為每個需要 VM 的小組成員從頭開始重建 VM 的額外成本相比，該增加成本可能微不足道。 例如，建立並儲存一個可供整個小組重複使用的 127 GB 映像，一個月只需幾塊錢。 不過，與每個員工投資在建置及驗證適當設定的開發環境以供其個人使用的時數相比，這些成本就顯得微不足道。

此外，您的開發工作或技術可能需要更大的規模，例如各種開發設定和多個機器設定。 您可以使用 Azure DevTest Labs 來建立「配方」，以自動建構您的「最佳映像」。 您也可以使用 DevTest Labs 來管理您小組執行中 VM 的原則。 [使用適用於開發人員的 Azure DevTest Labs](/azure/devtest-lab/devtest-lab-developer-lab) \(機器翻譯\) 是可供您了解 DevTest Labs 的最佳來源。

## <a name="next-steps"></a>後續步驟

既然您已了解預先設定的 Visual Studio 映像，下一步就是建立新的 VM：

* [透過 Azure 入口網站建立 VM](/azure/virtual-machines/windows/quick-create-portal)
* [Windows 虛擬機器概觀](/azure/virtual-machines/windows/overview)
