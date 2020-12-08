---
title: 設定電腦以開發 Office 方案
description: 瞭解如何安裝支援的 Visual Studio 版本、.NET Framework 和 Microsoft Office，讓您可以建立適用于 Microsoft Office 的 VSTO 增益集和自訂。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3658f655c50c9d1a0775a8cc69dd65baf32d1408
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847256"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>設定電腦以開發 Office 方案

若要為 Microsoft Office 建立 VSTO 增益集和自訂，請安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本。

|軟體|支援的版本|
|--------------|------------------------|
|Visual Studio 2017| 具有 **Office/SharePoint 開發** 工作負載的任何版本。|
|.NET Framework|-.NET Framework 4 或更新版本。|
|Microsoft Office|<ul><li>任何套件版本的 Office，包括適用于企業的 Microsoft 365 應用程式。</li><li>下列任何一種獨立應用程式：<br /><br /> <ul><li>Excel</li><li>InfoPath (僅限 Office 2013 和 Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> 必須在安裝 Office 時安裝 Visual Basic for Applications (VBA)。 **重要事項：** 不支援隨用隨之 Office 2010 應用程式的執行階段版本。|

如需詳細的安裝步驟，請參閱 [如何：設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>如果專案範本未出現或無法在 Visual Studio 中運作

如果您安裝受支援版本的 Visual Studio、.NET Framework 和 Microsoft Office，但 Office 專案範本不會出現在 Visual Studio [ **新增專案** ] 對話方塊中，或者在您嘗試使用時收到錯誤，請檢查下列各項：

- 確定電腦上已安裝 Microsoft Office 開發人員工具。

     Office developer tools 是 Visual Studio 的選用元件，但會隨 Visual Studio 自動安裝。 如果您透過指定要安裝的功能來自訂 Visual Studio 安裝，請確定已在安裝期間選擇 [Microsoft Office Developer Tools]  ，以安裝這些工具。

     若要確認已安裝這些工具，請啟動 Visual Studio 安裝程式，然後選擇 [ **修改** ] 按鈕。 選取 [Microsoft Office Developer Tools]  核取方塊，然後選擇 [更新]  按鈕。

- 確定您不是執行隨用隨的 Office 版本，而是由隨用隨之執行。 請參閱 [如何：確認 Outlook 是否為電腦上的隨時執行應用程式](/previous-versions/office/developer/office-2010/ff864733(v=office.14))。

- 確定您只執行一個版本的 Microsoft Office。

如果您持續遇到問題，請參閱 [Office 方案中錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)。

## <a name="see-also"></a>另請參閱
- [在 Visual Studio&#41;中開始 &#40;Office 開發 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [如何：設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [如何：安裝 Visual Studio Tools for Office 執行時間可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [如何：安裝 Office 主要 interop 元件](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)