---
title: Visual Studio Tools for Office 執行時間安裝案例
description: 瞭解如何安裝 Visual Studio 2010 Tools for Office runtime。 本文描述三種安裝案例。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448333"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office 執行時間安裝案例

  您可以用三種方式安裝適用于 Office 執行時間的 Visual Studio 2010 工具：

- 當您安裝 Visual Studio 時。

- 當您安裝 Microsoft Office 時。

- 當您安裝適用于 Office 執行時間可轉散發套件的 Visual Studio 2010 工具時。

  所安裝的執行階段元件取決於電腦組態和安裝情節。

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>每個安裝案例中安裝的執行時間元件

 適用于 Office 執行時間的 Visual Studio 2010 工具有三個元件： Office 方案載入器、適用于 .NET Framework 3.5 的 Office 擴充功能，以及適用于或更新版本的 Office 擴充功能 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 安裝執行階段時，一律會安裝 Office 方案載入器。 適用於 .NET Framework 的 Office 擴充功能之安裝取決於電腦組態和安裝情節。 當執行階段先安裝時，如果其中一個 Office 擴充功能無法安裝，則當符合特定需求時，執行階段會自動安裝遺失的 Office 擴充功能。 執行時間的這項功能稱為「 *隨選安裝*」。

 下表顯示每個執行階段安裝情節中預設會安裝的執行階段元件。 每個情節的詳細資訊稍後出現。

|執行階段的安裝情節|Office 方案載入器|適用於 .NET Framework 3.5 的 Office 擴充功能|適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Office 擴充功能|適用於 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 擴充功能|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|包含 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 和更新版本|是|是，如果 .NET Framework 3.5 已經安裝。|是|是|
|使用 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|是|是，如果 .NET Framework 3.5 已經安裝。|否|否|
|包含 Office 2010 Service Pack 1 (SP1) 或更新版本|是|是，如果 .NET Framework 3.5 已經安裝。|是，如果 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 已經安裝。|否|
|使用 Office 2013 和更新版本|是|是，如果 .NET Framework 3.5 已經安裝。|是，如果 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 已經安裝。|是，如果 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 已經安裝。|
|包含執行階段可轉散發套件|是|是，如果 .NET Framework 3.5 已經安裝。|是，如果 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 已經安裝。|是，如果 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 已經安裝。|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>使用 Visual Studio 或 Microsoft Office Developer Tools for Visual Studio 安裝執行時間

 當您在 Visual Studio 中安裝 Office Developer Tools 時，適用於 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 和 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Office 擴充功能一律安裝在開發電腦上。 只有當開發電腦上已經存在 .NET Framework 3.5 時，才會安裝適用於 .NET Framework 3.5 的 Office 擴充功能。 如果您在安裝 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 之後安裝 .NET Framework 3.5，則在第一次建立目標為 .NET Framework 3.5 的 Office 專案時，執行階段會自動安裝適用於 .NET Framework 3.5 的 Office 擴充功能。

> [!WARNING]
> 您無法使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 或更新版本建立以 .NET Framework 3.5 為目標的 Office 專案。

 如需有關如何安裝 Office developer tools 的詳細資訊，請參閱 [如何：設定電腦以開發 office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。

### <a name="install-the-runtime-with-office"></a>使用 Office 安裝執行時間

 當您安裝 Office 時，如果 .NET Framework 3.5 已存在於電腦上，則會安裝適用於 .NET Framework 3.5 的 Office 擴充功能。 如果您在安裝 Office 之後安裝 .NET Framework 3.5，執行階段會在 Office 應用程式第一次嘗試載入以 .NET Framework 3.5 為目標的方案時，自動安裝適用於 .NET Framework 3.5 的 Office 擴充功能。

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]如果電腦上已有對應的 .NET Framework 版本，則適用于或更新版本的 office 擴充功能也會隨 office 一起安裝。

 為確保您的使用者具有使用您應用程式所需的擴充功能，請將最新版的 Visual Studio 2010 Tools for Office runtime 可轉散發套件作為方案的必要條件。 如需必要條件的詳細資訊，請參閱 [Office 方案的部署必要條件](/previous-versions/bb608617(v=vs.110))。

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>使用執行時間可轉散發套件來安裝執行時間

 您可以手動執行 Visual Studio 2010 Tools for Office runtime 可轉散發套件，或在部署 Office 方案時包含可轉散發套件作為必要條件，以安裝執行時間。

 當您使用 Visual Studio 2010 Tools for Office runtime 可轉散發套件來安裝執行時間時， [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 如果電腦上已有對應的 .NET Framework 版本，則會安裝適用于 .NET Framework 3.5 的 office 擴充功能和適用于或更新版本的 office 擴充功能。 如果在安裝執行階段時電腦遺漏其中一種版本的 .NET Framework ，遺漏之 .NET Framework 版本的 Office 擴充功能不會在該時間安裝。 如果您稍後安裝遺漏的 .NET Framework 版本，則執行階段會在下一次安裝 (如果執行階段是隨使用 ClickOnce 部署的方案一起安裝) 或載入 (如果執行階段是隨使用 Windows Installer 部署的方案一起安裝) 需要此擴充功能的方案時自動安裝對應的 Office 擴充功能。

 如需在 ClickOnce 方案中包含必要條件的詳細資訊，請參閱 [如何：在終端使用者電腦上安裝必要條件以執行 Office 方案](/previous-versions/bb608608(v=vs.110))。 如需有關如何以手動方式從可轉散發套件安裝執行時間的詳細資訊，請參閱 [如何：安裝 Visual Studio Tools for Office 執行時間可](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)轉散發套件。

## <a name="see-also"></a>另請參閱

- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools for Office 執行時間中的元件](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
