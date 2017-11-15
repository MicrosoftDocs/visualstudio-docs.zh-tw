---
title: "安裝和設定測試代理程式 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 738cdab9bcc93408e1bb53df205328d2bc5e917f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="install-and-configure-test-agents"></a>安裝和設定測試代理程式

對於使用 Visual Studio 和 Visual Studio Team Services 或 Team Foundation Server (TFS) 的測試案例，您不需要測試控制器，因為 Agents for Microsoft Visual Studio 會與 Team Services 或 TFS 通訊以處理協調流程。 例如，您要使用 Team Services 或 TFS 中的組建和發行工作流程來執行連續測試。

如果您需要測試代理程式或測試控制器以使用 TFS 2013，請使用 Agents for Visual Studio 2013 Update 5 並設定測試控制器。

也請考慮[改用組建或發行管理](lab-management/use-build-or-rm-instead-of-lab-management.md)是否較為容易。

## <a name="what-do-i-need"></a>我需要什麼？

**在哪裡取得測試控制器和測試代理程式？**

* 如果您要使用組建 vNext 工作執行測試，而且想要從本機目錄安裝代理程式 - 

  * [下載 Agents for Microsoft Visual Studio 2015 RTM 和 Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266)。 

  * [下載 Agents for Microsoft Visual Studio 2017 和 Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs) - 選擇 [Tools for Visual Studio 2015]，然後從左側的瀏覽列選取 [Agents for Visual Studio 2015]。

* 如果您想要執行下列測試，請[下載 Agents for Microsoft Visual Studio 2013 Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264)：

  * 使用內部部署遠端電腦的負載測試。

  * 從遠端使用 Microsoft Test Manager 或 MSTest 及實驗室環境測試設定的連續測試。

  * 使用 TFS 2013 的連續測試。

這些安裝程式會以 ISO 檔案 (虛擬 CD) 提供，方便安裝在虛擬機器上。 

[可以混合使用 TFS、Microsoft Test Manager、測試控制器和測試代理程式的版本嗎？](#MixedVersions)

**安裝我的測試控制器和測試代理程式時有哪些系統需求？**

| 項目 | 需求 |
| ---- | ------------ |
| **代理程式** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2 Service Pack 1 |
| **控制器** | Windows 10<br />Windows 8、Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012、Windows Server 2012 R2<br />Windows Server 2008 Release 2 Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>問與答

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>問：可以混合使用 TFS、Microsoft Test Manager、測試控制器和測試代理程式的版本嗎？

答：可以，以下是支援的相容組合：

| TFS | 具有實驗室中心的 Microsoft Test Manager | 控制器 | 代理程式 |
| --- | -------------------------------------- | ---------- | ----- |
| 2015：從 2013 升級 | 2013 | 2013 |2013 |
| 2015：全新安裝 | 2013 | 2013 | 2013 |
| 2015：從 2013 升級或全新安裝 | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>問：Test Agent 2015 是否支援 Visual Studio 2013 的測試控制器和測試代理程式支援的所有案例？

答：建議您在所有新的自動化測試案例中使用 Agents for Visual Studio。 您可以使用組建定義中的「部署測試代理程式」工作，以下載並在電腦上安裝測試代理程式。
下表顯示 Agents for Visual Studio 2013 支援的案例，以及 Team Foundation Server (TFS) 2015 和 Team Services (TS) 的替代方案。

| Agents for Visual Studio 2013 所支援的案例 | TFS 和 TS 中的替代方案 |
| --- | --- |
| Visual Studio 中的建置-部署-測試工作流程 | 使用者可以使用[組建定義](https://www.visualstudio.com/team-services/continuous-integration/) (而非 XAML 組建) 來建置、部署和測試 TFS 中的案例。 |
| 使用內部部署遠端電腦的負載測試 (效能測試) | 使用 Test Controller/Test Agents 2013 Update 5 在內部部署執行負載測試。 [詳細資訊](https://msdn.microsoft.com/en-us/library/ff400223.aspx)。 |
| 使用實驗室環境從 Microsoft Test Manager 進行的自動化測試遠端執行 | 此案例目前沒有替代方案。 建議您在組建和發行定義 (而非 XAML 組建) 中使用「執行功能測試」工作，以從遠端執行測試。 |
| 在 Visual Studio 中執行遠端測試的開發人員 | 不再受支援。 |

<!-- ENDSECTION -->

## <a name="see-also"></a>請參閱

* [使用測試設定設定電腦和收集診斷資訊](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
