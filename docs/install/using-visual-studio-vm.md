---
title: "在 Azure 虛擬機器上使用 Visual Studio | Microsoft 文件"
description: "了解如何在 Azure 虛擬機器上使用 Visual Studio"
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Azure 上的 Visual Studio 映像
使用在預先設定的 Azure 虛擬機器 (VM) 中執行 Visual Studio，是開發環境從無到有的最簡單又最快的方法。  您可以在 [Azure Marketplace](https://portal.azure.com/) 中取得具有不同 Visual Studio 設定的系統映像。 只要啟動 VM，就可以開始使用。

第一次使用 Azure 嗎？ [建立免費的 Azure 帳戶](https://azure.microsoft.com/free)。

## <a name="what-configurations-and-versions-are-available"></a>哪些設定和版本可供使用？
在 Azure Marketplace 中，您可以找到最新主要版本 (Visual Studio 2017 和 Visual Studio 2015) 的映像。  針對每個主要版本，您會看到原始發行 (也稱為 'RTW') 版本，和「最新」更新版本。  針對每個這些不同版本，您會找到 Visual Studio Enterprise 和 Visual Studio Community 版本。  我們至少每個月更新這些映像，以包含最新的 Visual Studio 和 Windows 更新。  雖然映像名稱保持相同，但每個映像的描述都包含安裝的產品版本和映像的「起自」日期。

|               發行版本              |        版本       |     產品版本     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 - 最新 (15.5 版) | Enterprise、Community |      15.5.3 版     |
|         Visual Studio 2017 - RTW           | Enterprise、Community |      15.0.7 版     |
|   Visual Studio 2015 - 最新 (Update 3)   | Enterprise、Community |  14.0.25431.01 版  |
|         Visual Studio 2015 - RTW           |         無          | (維護已過期) |

> [!NOTE]
> 根據 Microsoft 維護原則，Visual Studio 2015 的原始發行 (亦稱為 'RTW') 版本的維護已過期。  因此，Visual Studio 2015 Update 3 是 Visual Studio 2015 產品線剩下唯一提供的版本。

如需詳細資訊，請參閱[Visual Studio IDE 維護原則](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs)。

## <a name="what-features-are-installed"></a>已安裝哪些功能？
每個映像都包含適用於該 Visual Studio 版本的建議功能集。  一般而言，安裝包含：

* 可用的工作負載，其中包含該工作負載的建議選用元件
* .NET 4.6.2 和 .NET 4.7 SDK、目標套件和開發人員工具
* Visual F#
* Visual Studio 的 GitHub 擴充
* LINQ to SQL 工具

這是我們在建置映像時用來安裝 Visual Studio 的命令列：

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

如果映像不包含您需要的 Visual Studio 功能，請透過意見反應工具 (頁面右上角) 提供意見反應。

## <a name="what-size-vm-should-i-choose"></a>我應該選擇的 VM 大小為何？
佈建新的虛擬機器很容易，且 Azure 提供一系列完整的虛擬機器大小。  如同取得任何硬體，您希望在效能和成本之間取得平衡。  由於 Visual Studio 是強大的多執行緒應用程式，建議您使用至少 2 個處理器和 7 GB 記憶體的 VM 大小。 在 Azure 中轉譯成至少這些 VM 大小：

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

如需最新機器大小的詳細資訊，請參閱 [Azure 中 Windows 虛擬機器的大小](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes)。

使用 Azure 時，您不會固定於第一次的挑選 - 您可以透過調整 VM 大小來重新平衡您的初始選擇。  您可以使用更適合的大小來佈建新的 VM，或者根據不同的底層硬體重新調整現有 VM 的大小。  如需詳細資訊，請參閱[調整 Windows VM 大小](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm)。

## <a name="after-i-get-the-vm-running-then-what"></a>在我讓 VM 開始執行之後，下一步是什麼？
Visual Studio 遵循 Azure 中的「自備授權」模型。  因此，與在專用硬體上安裝類似，第一個步驟是授權您的 Visual Studio 安裝。  您可以使用與 Visual Studio 訂閱相關聯的 Microsoft 帳戶登入來將 Visual Studio 解除鎖定，或者您可以使用最初購買的產品金鑰來將 Visual Studio 解除鎖定。  如需詳細資訊，請參閱[登入 Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio)和[如何：解除鎖定 Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio)。

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>建置開發 VM 之後，如何儲存 (擷取) 它以供日後或團隊使用？

開發環境的範圍很廣，而且建置更複雜環境的成本很高。  不過，不論您環境的設定為何，Azure 都可以儲存/擷取您精心設定的 VM，作為「基底映像」供日後自己或其他團隊成員使用，為您保留環境設定的投資。  然後，當您將新的 VM 開機時，即可從基底映像佈建它，而不是 Marketplace 映像。

讓我們快速摘要說明，您需要執行 sysprep 並將執行中的 VM 關機，然後透過 Azure 入口網站的 UI *擷取 (圖 1)* 該 VM 作為映像。  Azure 會將包含該映像的 `.vhd` 檔案儲存在您所選擇的儲存體帳戶中。  然後，新映像會在您訂用帳戶的資源清單中顯示為映像資源。

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(圖 1) 透過 Azure 入口網站的 UI 擷取映像。*</center>

如需詳細資訊，請參閱[擷取 VM 至映像](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource) \(機器翻譯\)。

  **提醒：**記得對 VM 執行 sysprep！  如果您未執行該步驟，Azure 便無法從該映像佈建 VM。

> [!NOTE]
> 您仍然需要為該映像的儲存空間花費一些成本，但累加的成本應遠小於為團隊中需要 VM 的每個人從頭建置 VM 花費的人力成本。  例如，建立並儲存一個 127 GB 供團隊成員重複使用的映像，每個月只需幾塊美元。  不過，這些成本遠小於每個員工投資數小時來建置及驗證是否已適當設定供他們自己使用的開發電腦。

此外，您的開發工作或技術可能需要更多調整，例如各種開發設定和多個機器設定。  您可以使用 Azure DevTest Labs 來建立「配方」，以自動化「黃金映像」的建立，並管理團隊執行中 VM 的原則。  [使用適用於開發人員的 Azure DevTest Labs](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) \(機器翻譯\) 是取得 DevTest Labs 詳細資訊的最佳資源。

## <a name="next-steps"></a>後續步驟
您已經了解預先設定的 Visual Studio 映像，下一步是建立新的 VM：

* [使用 Azure 入口網站建立 Windows 虛擬機器](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Windows 虛擬機器概觀](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
