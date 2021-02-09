---
title: 安裝測試代理程式和測試控制器
description: 瞭解如何使用 Visual Studio 代理程式來協調 Azure Test Plans 或 Team Foundation Server 的測試。
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29f4951fbd64bd02c8f70b93ea319ab0d46f89e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920429"
---
# <a name="install-test-agents-and-test-controllers"></a>安裝測試代理程式和測試控制器

針對使用 Visual Studio 和 Azure Test Plans 或 Team Foundation Server (TFS) 的測試案例，您不需要測試控制器。 Agents for Visual Studio 能夠與 Azure Test Plans 或 TFS 通訊來處理協調流程。 一種可能的案例是您在 Azure Test Plans 或 TFS 中執行建置和發行工作流程的持續測試。

建議您也可考慮使用[建置或發行管理](use-build-or-rm-instead-of-lab-management.md)是否更為適合，而不是 Lab Management。

## <a name="system-requirements"></a>系統需求

下表顯示安裝適用於 Visual Studio 之測試代理程式或測試控制器的系統需求：

| 項目 | 規格需求 |
| ---- | ------------ |
| **代理程式** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard 和 Datacenter<br />Windows Server 2012 R2 |
| **控制器** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard 和 Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>安裝測試控制器和測試代理程式

您可以從 [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents) 下載 Agents for Visual Studio。 尋找 *Agents for Visual Studio 2019*，選取 [代理程式] 或 [控制器]，然後選擇 [下載]。 執行下載的可執行檔以安裝測試代理程式或控制器。

您可以從[舊版下載](https://visualstudio.microsoft.com/vs/older-downloads/)頁面下載 Agents for Visual Studio 2017、Visual Studio 2015 和 Visual Studio 2013。

這些安裝程式會以 ISO 檔案提供，方便安裝在虛擬機器上。

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>TFS、Microsoft Test Manager、測試控制器和測試代理程式的相容版本

您可以根據下表，混合使用不同版本的 TFS、Microsoft Test Manager、測試控制器和測試代理程式：

| TFS | 具有實驗室中心的 Microsoft Test Manager | 控制器 | 代理程式 |
| --- | -------------------------------------- | ---------- | ----- |
| 2017：從 2015 升級或全新安裝 | 2017 | 2017 | 2017 |
| 2017：從 2015 升級或全新安裝 | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017：從 2015 升級或全新安裝 | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015：從 2013 升級 | 2013 | 2013 |2013 |
| 2015：全新安裝 | 2013 | 2013 | 2013 |
| 2015：從 2013 升級或全新安裝 | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>TFS、測試控制器和測試代理程式的相容版本

您可以根據下表，混合使用不同版本的 TFS、測試控制器和測試代理程式：

| TFS | 控制器 | 代理程式 |
| --- | -------------------------------------- | ---------- | ----- |
| 2017：從 2015 升級或全新安裝 | 2017 | 2017 |
| 2017：從 2015 升級或全新安裝 | 2013 Update 5 | 2013 Update 5 |
| 2017：從 2015 升級或全新安裝 | 2013 Update 5 | 2013 Update 5 |
| 2015：從 2013 升級 | 2013 |2013 |
| 2015：全新安裝 | 2013 | 2013 |
| 2015：從 2013 升級或全新安裝 | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> TFS 2018 和 Azure DevOps Services 中的 Lab management 案例已淘汰。 如需詳細資訊，請參閱 [TFS 2018 版本資訊](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager)。

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>從 Visual Studio 2013 測試代理程式升級

建議您在所有新的自動化測試案例中使用 Agents for Visual Studio。 您可以使用組建管線中的「部署測試代理程式」工作來下載並在電腦上安裝測試代理程式。

下表顯示 Agents for Visual Studio 2013 支援的案例，以及 Team Foundation Server (TFS) 2015 和 Test Plans 的替代方案：

| Agents for Visual Studio 2013 所支援的案例 | TFS 和 Azure Test Plans 中的替代方案 |
| - | - |
| Visual Studio 中的建置-部署-測試工作流程 | 使用者可以使用[組建管線](/azure/devops/pipelines/index?view=vsts&preserve-view=true) (而非 XAML 組建) 來建置、部署和測試 TFS 中的案例。 |
| 使用內部部署遠端電腦的負載測試 (效能測試) | 使用 Test Controller 和 Test Agents 2013 Update 5 在內部部署執行負載測試。 |
| 使用實驗室環境 Microsoft Test Manager (在 Visual Studio 2017) 中淘汰的自動化測試遠端執行 | 此案例目前沒有替代方案。 建議您在組建和發行定義 (而非 XAML 組建) 中使用「執行功能測試」工作，以從遠端執行測試。 |
| 在 Visual Studio 中執行遠端測試的開發人員 | 不再支援。 |
