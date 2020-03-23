---
title: Visual Studio 工作負載與元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.custom: seodec18
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b9af7c981e92495d07d0f0d455251e494aa4cc7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79485899"
---
# <a name="visual-studio-workload-and-component-ids"></a>Visual Studio 工作負載與元件識別碼

按一下下表中的版本名稱，以查看使用命令列來安裝 Visual Studio 或是在 VSIX 資訊清單中指定為相依性時，將會需要的可用工作負載和元件識別碼。

::: moniker range="vs-2017"

**更新[15.9 版本](/visualstudio/releasenotes/vs2017-relnotes/)**

| **版本** | **識別碼** | **描述** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md?vs-2017) | Microsoft.VisualStudio.Product.Enterprise | 適用於任何規模之小組間的生產力和協調的 Microsoft DevOps 方案 |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md?vs-2017) | Microsoft.VisualStudio.Product.Professional | 適用於小型小組的專業開發人員工具和服務 |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | 功能完整的免費 IDE，適用於學生、開放原始碼及個人開發人員 |
| [視覺&nbsp;工作室團隊&nbsp;資源管理器&nbsp;2017](workload-component-id-vs-team-explorer.md?vs-2017) | Microsoft.VisualStudio.Product.TeamExplorer | 在不使用 Visual Studio 開發人員工具組的情況下，與 Team Foundation Server 和 Azure DevOps Services 互動 |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md?vs-2017) | Microsoft.VisualStudio.Product.WDExpress | 透過語法感知程式碼編輯、原始程式碼控制以及工作項目管理，建置原生和 Managed 應用程式，例如 WPF、WinForms 和 Win32。 包含 C#、Visual Basic 和 Visual C++ 的支援。 |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md?vs-2017) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools 可讓您建置原生和受管理 MSBuild 型應用程式，而不需要 Visual Studio IDE。 您可以選擇安裝 Visual C++ 編譯器及程式庫、MFC、ATL 以及 C++/CLI 支援。 |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2017](workload-component-id-vs-test-agent.md?vs-2017)  | Microsoft.VisualStudio.Product.TestAgent | 支援在遠端執行自動化的測試與負載測試 |
| [視覺&nbsp;工作室測試&nbsp;控制器 2017](workload-component-id-vs-test-controller.md?vs-2017) | Microsoft.VisualStudio.Product.TestController | 將自動化的測試散發至多部電腦 |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md?vs-2017) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md?vs-2017) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

如需如何使用這些清單的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) 頁面和[如何：將擴充性專案移轉到 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2017) 頁面。

::: moniker-end

::: moniker range="vs-2019"

**更新[16.5 版本](/visualstudio/releases/2019/release-notes/)**

| **版本** | **識別碼** | **描述** |
| ----------- | ------ | --------------- |
| [視覺&nbsp;工作室企業&nbsp;2019](workload-component-id-vs-enterprise.md?vs-2019) | Microsoft.VisualStudio.Product.Enterprise | 適用於任何規模之小組間的生產力和協調的 Microsoft DevOps 方案 |
| [視覺&nbsp;工作室專業&nbsp;2019](workload-component-id-vs-professional.md?vs-2019) | Microsoft.VisualStudio.Product.Professional | 適用於小型小組的專業開發人員工具和服務 |
| [視覺&nbsp;工作室社區&nbsp;2019](workload-component-id-vs-community.md?vs-2019) | Microsoft.VisualStudio.Product.Community | 功能完整的免費 IDE，適用於學生、開放原始碼及個人開發人員 |
| [視覺&nbsp;工作室團隊&nbsp;資源管理器&nbsp;2019](workload-component-id-vs-team-explorer.md?vs-2019) | Microsoft.VisualStudio.Product.TeamExplorer | 在不使用 Visual Studio 開發人員工具組的情況下，與 Team Foundation Server 和 Azure DevOps Services 互動 |
| [視覺&nbsp;工作室構建&nbsp;工具&nbsp;2019](workload-component-id-vs-build-tools.md?vs-2019) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools 可讓您建置原生和受管理 MSBuild 型應用程式，而不需要 Visual Studio IDE。 您可以選擇安裝 Visual C++ 編譯器及程式庫、MFC、ATL 以及 C++/CLI 支援。 |
| [視覺&nbsp;工作室測試&nbsp;代理&nbsp;2019](workload-component-id-vs-test-agent.md?vs-2019)  | Microsoft.VisualStudio.Product.TestAgent | 支援在遠端執行自動化的測試與負載測試 |
| [視覺化&nbsp;工作室負載&nbsp;測試&nbsp;控制器 2019](workload-component-id-vs-test-controller.md?vs-2019) | Microsoft.VisualStudio.Product.TestController | 將自動化的測試散發至多部電腦 |

有關如何使用這些清單的詳細資訊，請參閱[使用命令列參數以安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)頁和["如何：將擴充性專案遷移到視覺化工作室](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2019)"頁。

> [!NOTE]
> 如需先前版本的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md?view=vs-2017)

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 的 Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝視覺化工作室](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [創建視覺化工作室的離線安裝](create-an-offline-installation-of-visual-studio.md)
