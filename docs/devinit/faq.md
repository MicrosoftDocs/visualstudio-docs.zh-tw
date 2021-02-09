---
title: 常見問題集
description: Devinit 工具的常見問題。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98d61d86b894dc989e24aef809e0f97fd513f481
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932973"
---
# <a name="frequently-asked-questions-for-devinit"></a>Devinit 的常見問題

## <a name="is-devinit-just-for-github-codespaces"></a>Devinit 僅適用于 GitHub Codespaces 嗎？

目前，devinit 僅提供作為 GitHub Codespaces 私用 Beta 的一部分。 不過，我們計畫在即將推出的 Visual Studio 2019 版本中包含 devinit。

## <a name="is-it-windows-only"></a>它是否僅限 Windows？
是的，devinit 著重于建立開發人員環境，以供使用 Visual Studio 的開發人員使用，這表示 Windows。 我們正在考慮其他平臺，但其中有許多都已備妥絕佳的解決方案，所以我們想要從 Visual Studio 和 Windows 開始著手。

## <a name="theres-no-tool-for-the-dependency-i-need"></a>我需要的相依性沒有工具！

很抱歉！ 如果您是 GitHub Codespaces 私用 Beta 的一部分，您可以透過私人 Beta 的意見反應管道取回我們。 如果您不是私用 Beta 的一部分，我們仍然喜歡您對所需內容的意見反應，而您可以在我們的 [Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) 檔提出問題，並提供標籤 `devinit` 來要求支援您所需的工具。

## <a name="something-went-wrong-how-do-i-debug"></a>發生錯誤，如何進行調試？

如果 devinit 失敗，要嘗試的第一件事就是 `--verbose / -v` 取得詳細資訊的旗標。 Devinit 正在呼叫的基礎工具可能遇到問題。 詳細資訊記錄檔資訊應包含接下來要查看的線索。

## <a name="why-not-just-a-script"></a>為什麼不是腳本呢？

透過腳本設定環境是一段時間的技術，而且可以發揮最大效果。 如果適合您，請使用！ devinit 是開發人員在腳本不是最佳選擇時的另一個選項。

## <a name="why-not-a-container"></a>為何要使用容器？

容器和 Docker 是透過程式碼部署環境的絕佳工具。 有幾個原因會導致容器可能不是適合您的解決方案：

1. 如果您想要使用 Windows 桌面開發環境。
1. 如果您已經有作業系統，而且只想要調整，而不是部署新的環境。

基於這些原因，devinit 是關於自訂您目前擁有的 Windows 環境。

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>其他 VM 建立工具的相關資訊 (例如 Terraform、Packer、Chef、Vagrant 等等 ) 

建立 Windows 映像有許多絕佳的工具，您應該使用它們！ 但是，我們找不到可滿足我們所述之所有案例的人。 我們希望 devinit 是一種工具，可讓開發人員使用特定存放庫所需的任何內容來自訂其環境，並與 Visual Studio 有絕佳的整合，而不是建立 VM 映射的工具。

## <a name="what-about-winget"></a>Winget 呢？

devinit 不是套件管理員（例如 winget），我們也不想要。 我們希望您能夠使用 winget 搭配 devinit，而且我們正在處理一種工具。

## <a name="how-are-restarts-handled"></a>如何處理重新開機？

如果 devinit 安裝的任何程式都需要重新開機作業系統，則會將錯誤訊息輸出至主控台。 然後，您必須在適合您的時間重新開機作業系統。 重新開機之後，如果未安裝所有相依性，您可能需要重新執行 devinit。

## <a name="working-with-others"></a>與他人合作

devinit 的所有功能都是為了讓您能夠使用廣泛的生態系統，來部署和設定您的應用程式可能會有的相依性。 雖然 devinit 對它所提供的內容有意見，但 devinit 大多是要從宣告式 JSON 檔案中執行其他工具。

今天，devinit 剛開始著手，我們 [的工具清單](devinit-tool-list.md) 只是一開始。
