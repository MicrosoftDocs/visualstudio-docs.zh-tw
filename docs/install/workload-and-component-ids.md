---
title: Visual Studio 工作負載與元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 3/2/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.custom: seodec18
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.prod: visual-studio-windows
ms.technology: vs-installation
open_to_public_contributors: false
ms.openlocfilehash: be97c0c56395a9fe87633ccf48f0382b15fae560
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683681"
---
# <a name="visual-studio-workload-and-component-ids"></a>Visual Studio 工作負載與元件識別碼

按一下下表中的版本名稱，以查看使用命令列來安裝 Visual Studio 或是在 VSIX 資訊清單中指定為相依性時，將會需要的可用工作負載和元件識別碼。

::: moniker range="vs-2017"

**[15.9 版](/visualstudio/releasenotes/vs2017-relnotes/)的更新**

| **版本(Edition)** | **識別碼** | **說明** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.Enterprise | 適用於任何規模之小組間的生產力和協調的 Microsoft DevOps 方案 |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.Professional | 適用於小型小組的專業開發人員工具和服務 |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.Community | 功能完整的免費 IDE，適用於學生、開放原始碼及個人開發人員 |
| [Visual &nbsp; Studio Team &nbsp; Explorer &nbsp; 2017](workload-component-id-vs-team-explorer.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.TeamExplorer | 在不使用 Visual Studio 開發人員工具組的情況下，與 Team Foundation Server 和 Azure DevOps Services 互動 |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.WDExpress | 透過語法感知程式碼編輯、原始程式碼控制以及工作項目管理，建置原生和 Managed 應用程式，例如 WPF、WinForms 和 Win32。 包含 C#、Visual Basic 和 Visual C++ 的支援。 |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools 可讓您建置原生和受管理 MSBuild 型應用程式，而不需要 Visual Studio IDE。 您可以選擇安裝 Visual C++ 編譯器及程式庫、MFC、ATL 以及 C++/CLI 支援。 |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2017](workload-component-id-vs-test-agent.md?view=vs-2017&preserve-view=true)  | Microsoft.VisualStudio.Product.TestAgent | 支援在遠端執行自動化的測試與負載測試 |
| [Visual &nbsp; Studio Test &nbsp; Controller 2017](workload-component-id-vs-test-controller.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.TestController | 將自動化的測試散發至多部電腦 |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md?view=vs-2017&preserve-view=true) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

如需如何使用這些清單的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) 頁面和[如何：將擴充性專案移轉到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2017&preserve-view=true) 頁面。

::: moniker-end

::: moniker range="vs-2019"

**[16.8 版](/visualstudio/releases/2019/release-notes/)的更新**

| **版本(Edition)** | **識別碼** | **說明** |
| ----------- | ------ | --------------- |
| [Visual &nbsp; Studio Enterprise &nbsp; 2019](workload-component-id-vs-enterprise.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.Enterprise | 適用於任何規模之小組間的生產力和協調的 Microsoft DevOps 方案 |
| [Visual &nbsp; Studio Professional &nbsp; 2019](workload-component-id-vs-professional.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.Professional | 適用於小型小組的專業開發人員工具和服務 |
| [Visual &nbsp; Studio 社區 &nbsp; 2019](workload-component-id-vs-community.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.Community | 功能完整的免費 IDE，適用於學生、開放原始碼及個人開發人員 |
| [Visual &nbsp; Studio Team &nbsp; Explorer &nbsp; 2019](workload-component-id-vs-team-explorer.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.TeamExplorer | 在不使用 Visual Studio 開發人員工具組的情況下，與 Team Foundation Server 和 Azure DevOps Services 互動 |
| [Visual &nbsp; Studio Build &nbsp; Tools &nbsp; 2019](workload-component-id-vs-build-tools.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools 可讓您建置原生和受管理 MSBuild 型應用程式，而不需要 Visual Studio IDE。 您可以選擇安裝 Visual C++ 編譯器及程式庫、MFC、ATL 以及 C++/CLI 支援。 |
| [Visual &nbsp; Studio Test &nbsp; Agent &nbsp; 2019](workload-component-id-vs-test-agent.md?view=vs-2019&preserve-view=true)  | Microsoft.VisualStudio.Product.TestAgent | 支援在遠端執行自動化的測試與負載測試 |
| [Visual &nbsp; Studio 負載 &nbsp; 測試 &nbsp; 控制器2019](workload-component-id-vs-test-controller.md?view=vs-2019&preserve-view=true) | Microsoft.VisualStudio.Product.TestController | 將自動化的測試散發至多部電腦 |

如需如何使用這些清單的詳細資訊，請參閱 [使用命令列參數安裝 Visual studio](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) 頁面和如何：將擴充性 [專案遷移至 visual studio](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2019&preserve-view=true) 頁面。

> [!NOTE]
> 如需先前版本的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md?view=vs-2017&preserve-view=true)

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 的 Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
