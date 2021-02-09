---
title: GitHub Codespaces (Preview) 總覽
description: 深入瞭解 GitHub Codespaces Visual Studio，以及它如何協助將您的開發環境延伸到雲端。
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 374e07735667a2a8891824b23d49b061651b3b95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911720"
---
# <a name="what-is-github-codespaces-preview"></a>什麼是 GitHub Codespaces？ (預覽)

歡迎使用 Codespaces！ 很高興您在這裡。

GitHub Codespaces 可為您提供適用于任何活動的雲端技術開發環境，不論是長期專案，還是審核提取要求等短期工作。 您可以從 Visual Studio 2019 Preview 內使用 codespace ([註冊有限的公用 Beta](https://github.com/features/codespaces/signup-vs)) 。

此外，GitHub Codespaces 帶來許多 DevOps 的優點，例如重複性和可靠性， &mdash; 通常會保留給開發環境的生產工作負載 &mdash; 。 您也可以將 GitHub Codespaces 個人化，讓您偏好及依賴的工具、程式和設定也存在。

本檔將說明重要概念，並介紹 Codespaces 功能。 如果您想要開始使用，請參閱 [使用 Visual Studio codespace](use-visual-studio-with-codespaces.md)。

> [!IMPORTANT]
> 您必須註冊有限的 [公用 Beta 版](https://github.com/features/codespaces/signup-vs) ，才能使用 GitHub Codespaces。 在測試期間，GitHub 不會對 Codespaces 的可用性做出任何保證。 如需有關加入 Beta 的詳細資訊，請參閱 [關於 Codespaces](https://docs.github.com/github/developing-online-with-codespaces/about-codespaces#joining-the-beta)。

## <a name="concepts-and-features"></a>概念和功能

GitHub Codespaces 功能是以一些基本概念為基礎。 本節涵蓋這些概念，並提供功能的簡短導覽。

### <a name="remote-development"></a>遠端開發

現今許多開發人員都嘗試在以特定開發和執行時間堆疊設定的遠端設定或 Vm 中撰寫程式碼。 因為它太難、過度干擾，而且在某些情況下，在本機設定這些開發環境幾乎不可能發生。 此外，個人還想要試用新的技術或新的架構，而不必擔心「因為各家」他們的日常工作所需的機器。

雖然使用遠端環境和遠端功能的工具可讓開發人員使用，但通常會造成機器管理的額外負荷。 環境設定通常會讓上線和內容切換變得複雜。 GitHub Codespaces 可讓許多環境同時存在，以移除快速上線和內容切換的阻礙。 

GitHub Codespaces 提供受控解決方案，可讓您專注于設定的生產力。 GitHub Codespaces 在概念上和技術上擴充了 Visual Studio 2019 以進行遠端開發。 

### <a name="about-codespaces"></a>關於 codespaces

Codespace 是 GitHub Codespaces 的「後端」一半。 所有與軟體發展相關聯的計算都會在這裡進行：編譯、偵測、還原等等。建立 codespace 可準備完成工作所需的一切，並檢查 PR 或開始新專案。 Codespaces 設定執行時間、編譯器、偵錯工具、編輯器、自訂 dotfile 設定，以及處理專案所需的原始程式碼。

雲端託管的 codespaces 提供下列優點：

- 它們很快就能建立和處置。  (最多可建立帳戶限制) ，然後在完成時處置它們。
- 它們是受管理的，可減少您的整體維護。
- 它們具有可預測的定價，您只需支付使用的部分。 此外，也有內建的 autosuspend 可消除失控成本。
- 他們會儲存計算資源。 當您將開發工作負載移至雲端時，它會釋出您個人電腦上的有限資源。

## <a name="custom-configuration"></a>自訂組態

GitHub Codespaces 的設計是為了容納各種不同的專案或工作。 您可以從提供一般預設值的智慧型設定功能開始，或使用 [自訂](customize-codespaces.md)設定來微調 codespace。

彈性的設定可讓開發人員快速上架具有獨特設定和需求的專案，而這些專案很難在本機電腦上套用。 此外，可重現的 codespaces 消除了「在我的電腦上運作」問題。

## <a name="personal-configuration"></a>個人設定

我們知道在雲端裝載的 codespace 上進行開發時，您可以放心地保留個人喜好設定。 GitHub Codespaces 會將個人化自訂分層置於 codespace 設定的最上層。 GitHub Codespaces 支援編輯器和終端機的個人喜好設定和設定。

您可以使用 [自訂 (dotfile](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) 的使用者專屬集合來建立 codespace，例如、 `.bashrc` `.gitconfig` 、等等 ) ，而 GitHub Codespaces 會自動同步處理您的 Git 身分識別、主題和設定，讓您所建立的每個 codespace 無論專案特定的環境功能為何，都能以您想要的方式顯示並感覺。

## <a name="see-also"></a>另請參閱

* [如何搭配 codespace 使用 Visual Studio](use-visual-studio-with-codespaces.md)
* [如何自訂 codespace](customize-codespaces.md)
* [支援的 Visual Studio 功能](supported-features-codespaces.md)
