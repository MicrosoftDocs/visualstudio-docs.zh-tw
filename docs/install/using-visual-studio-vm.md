---
title: 在 Azure 虛擬機器上使用 Visual Studio
titleSuffix: ''
description: 了解如何在 Azure 虛擬機器上使用 Visual Studio
ms.date: 02/19/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12d99cf2e15bf1d806035598f9c92b5ed3319d25
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450395"
---
# <a id="top"> </a> Azure 上的 Visual Studio 映像

若要從無到有地建立開發環境，在預先設定的 Azure 虛擬機器 (VM) 中使用 Visual Studio，是既簡單又快速的方法。 您可以在 [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1) 中取得具有不同 Visual Studio 設定的系統映像。

第一次使用 Azure 嗎？ [建立免費的 Azure 帳戶](https://azure.microsoft.com/free)。

## <a name="what-configurations-and-versions-are-available"></a>哪些設定和版本可供使用？

您可以在 Azure Marketplace 中找到最新主要版本 (Visual Studio 2017 和 Visual Studio 2015) 的映像。  我們最近新增了即將推出的主要版本：Visual Studio 2019 預覽版支援。  針對每個已發行的主要版本，您都會看見原始發行 (RTW) 版本及最新更新的版本。  這些版本每個都會提供 Visual Studio Enterprise 和 Visual Studio Community 版本。  這些映像每個月至少都會更新一次，以包含最新的 Visual Studio 和 Windows 更新。  雖然映像名稱保持相同，但每個映像的描述都包含安裝的產品版本和映像的「起自」日期。

| 發行版本                                              | 版本                     |     產品版本      |
|:------------------------------------------------------------:|:----------------------------:|:------------------------:|
|    Visual Studio 2019：預覽版 (Preview 3)                   |           企業         | 16.0.0 Preview 3 版 |
| Visual Studio 2017：最新版本 (版本 15.9)                    |    Enterprise、Community     |      15.9.7 版      |
|         Visual Studio 2017：RTW                              |    Enterprise、Community     |      15.0.20 版     |
|   Visual Studio 2015：最新版本 (Update 3)                      |    Enterprise、Community     |  14.0.25431.01 版   |
|         Visual Studio 2015：RTW                              |             無             | (維護已過期)  |

> [!NOTE]
> 根據 Microsoft 維護原則，Visual Studio 2015 的原始發行 (RTW) 版本的維護已過期。 Visual Studio 2015 Update 3 是 Visual Studio 2015 產品線剩下唯一提供的版本。

如需詳細資訊，請參閱[Visual Studio IDE 維護原則](/visualstudio/productinfo/vs-servicing-vs)。

## <a name="what-features-are-installed"></a>已安裝哪些功能？

每個映像都包含適用於該 Visual Studio 版本的建議功能集。 一般而言，安裝包含：

* 所有可用的工作負載，包含每個工作負載的建議選擇性元件
* .NET 4.6.2 和 .NET 4.7 SDK、目標套件和開發人員工具
* Visual F#
* Visual Studio 的 GitHub 延伸模組
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

如果映像不包含您需要的 Visual Studio 功能，請透過位於頁面右上角的意見反應工具提供意見反應。

## <a name="what-size-vm-should-i-choose"></a>我應該選擇的 VM 大小為何？

Azure 提供完整的虛擬機器大小範圍。 由於 Visual Studio 是強大的多執行緒應用程式，建議您使用至少包含兩個處理器和 7 GB 記憶體的 VM 大小。 針對 Visual Studio 映像，我們建議使用下列 VM 大小：

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

如需最新機器大小的詳細資訊，請參閱 [Azure 中 Windows 虛擬機器的大小](/azure/virtual-machines/windows/sizes)。

使用 Azure 時，您可以透過調整 VM 大小來重新平衡您的初始選擇。 您可以使用更適合的大小來佈建新的 VM，或者針對不同的底層硬體重新調整現有 VM 的大小。 如需詳細資訊，請參閱[調整 Windows VM 大小](/azure/virtual-machines/windows/resize-vm)。

## <a name="after-the-vm-is-running-whats-next"></a>在 VM 執行之後，下一步是什麼？

Visual Studio 遵循 Azure 中的「自備授權」模型。 與在專用硬體上安裝類似，其中一個應先採取的步驟，便是授權您的 Visual Studio 安裝。 若要解除 Visual Studio 的鎖定，請執行下列其中一項動作：
- 使用與 Visual Studio 訂用帳戶相關聯的 Microsoft 帳戶登入
- 使用您最初購買時所隨附的產品金鑰，來解除 Visual Studio 的鎖定

如需詳細資訊，請參閱[登入 Visual Studio](../ide/signing-in-to-visual-studio.md) 和[如何解除鎖定 Visual Studio](../ide/how-to-unlock-visual-studio.md)。

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>我該如何儲存開發 VM，以供未來或團隊使用？

開發環境的範圍很廣，而且建置更複雜環境的成本很高。 無論環境的設定為何，您都可以將自己已設定的 VM 儲存或擷取為「基底映像」，以供未來或團隊的其他成員使用。 然後，當您將新的 VM 開機時，便可以從基底映像佈建它，而不是使用 Azure Marketplace 映像。

快速摘要：使用系統準備工具 (Sysprep) 並將執行中的 VM 關機，然後透過 Azure 入口網站中的 UI 將 VM 擷取 (圖 1) 為映像。 Azure 會將包含該映像的 `.vhd` 檔案儲存在您所選擇的儲存體帳戶中。 新映像會在您訂用帳戶的資源清單中顯示為映像資源。

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(圖 1) 透過 Azure 入口網站的 UI 擷取映像。*</center>

如需詳細資訊，請參閱[在 Azure 中建立一般化 VM 的受控映像](/azure/virtual-machines/windows/capture-image-resource)。

> [!IMPORTANT]
> 請不要忘了使用 Sysprep 來準備該 VM。 如果您未執行該步驟，Azure 便無法從該映像佈建 VM。

> [!NOTE]
> 您仍然需要為該映像的儲存空間花費一些成本，但累加的成本會遠小於針對團隊中需要 VM 的每個人員從頭建置 VM 所花費的額外成本。 例如，建立並儲存一個 127 GB 供全體團隊成員重複使用的映像，每個月會需要花費幾塊美元。 不過，這些成本遠小於每個員工投資數小時來建置及驗證是否已適當設定供他們自己使用的開發電腦。

此外，您的開發工作或技術可能需要更多調整，例如各種開發設定和多個機器設定。 您可以使用 Azure DevTest Labs 來建立_配方_，以自動化您「黃金映像」的建立。 您也可以使用 DevTest Labs 來管理團隊執行中 VM 的原則。 [使用適用於開發人員的 Azure DevTest Labs](/azure/devtest-lab/devtest-lab-developer-lab) \(機器翻譯\) 是取得 DevTest Labs 詳細資訊的最佳資源。

## <a name="next-steps"></a>後續步驟

您已經了解預先設定的 Visual Studio 映像，下一步是建立新的 VM：

* [使用 Azure 入口網站建立 Windows 虛擬機器](/azure/virtual-machines/windows/quick-create-portal)
* [Windows 虛擬機器概觀](/azure/virtual-machines/windows/overview)
