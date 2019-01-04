---
title: 設定電腦以開發 Office 方案
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47435fb5767b19ca36fc94387bdbefe3578f6325
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955941"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>設定電腦以開發 Office 方案

若要為 Microsoft Office 建立 VSTO 增益集和自訂，請安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本。

|軟體|支援的版本|
|--------------|------------------------|
|Visual Studio 2017| 使用任何版本**Office/SharePoint 開發**工作負載。|
|.NET Framework|-.NET Framework 4 或更新版本。|
|Microsoft Office|<ul><li>任何 Office 套件版本，包括 Office Professional Plus for Office 365。</li><li>下列任何一種獨立應用程式：<br /><br /> <ul><li>Excel</li><li>InfoPath (僅限 Office 2013 和 Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>專案</li><li>Visio</li><li>Word</li></ul></li></ul><br /> 必須在安裝 Office 時安裝 Visual Basic for Applications (VBA)。 **重要：** 不支援隨選即用版本的 Office 2010 應用程式。|

如需詳細的安裝步驟，請參閱[How to:設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>如果未顯示專案範本，或無法在 Visual Studio

如果您安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本，但 Office 專案範本未顯示在 Visual Studio**新的專案** 對話方塊中，或您收到錯誤時嘗試使用其中一個，請檢查下列項目：

- 確定電腦上已安裝 Microsoft Office 開發人員工具。

     Office 開發人員工具是 Visual Studio 中的選擇性元件，但隨著 Visual Studio 會自動安裝。 如果您透過指定要安裝的功能來自訂 Visual Studio 安裝，請確定已在安裝期間選擇 [Microsoft Office Developer Tools]  ，以安裝這些工具。

     若要確定已安裝這些工具，啟動 Visual Studio 安裝程式，然後選擇**修改** 按鈕。 選取 [Microsoft Office Developer Tools]  核取方塊，然後選擇 [更新]  按鈕。

- 請確定您不執行的隨選按一下可執行的 Office 版本。 請參閱[如何：請檢查 Outlook 是否在電腦上的按一下 執行應用程式](/previous-versions/office/developer/office-2010/ff864733(v=office.14))。

- 請確定您執行只有一個版本的 Microsoft Office。

如果您仍然遇到問題，請參閱[Office 方案錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)。

## <a name="see-also"></a>另請參閱

[開始使用&#40;在 Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[如何：設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[如何：安裝 Visual Studio Tools for Office runtime 可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[如何：安裝 Office 主要 interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)
