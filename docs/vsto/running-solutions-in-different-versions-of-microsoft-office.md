---
title: 在不同版本的 Microsoft Office 中執行解決方案
description: 瞭解如何執行使用 Visual Studio 2010 和更新版本所建立 Microsoft Office 解決方案的版本。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d70e61e318f0f6afd0a58ed35f912b6a5f2cda8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523538"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>在不同版本的 Microsoft Office 中執行解決方案

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>執行使用 Visual Studio 2010 和更新版本所建立的 Office 方案

|專案範本的目標 Office 版本|專案<sup>1</sup>的目標 .NET Framework|可以執行方案的 Office 版本|終端使用者電腦上的必要執行時間|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 和 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office 系統<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office 系統<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|
|2007 Microsoft Office system|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] (含) 以後版本<br /><br /> 或<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime|

 1. 使用者電腦上必須有您專案的目標 .NET Framework 版本，您的方案才能執行。 例如，如果您的專案以 .NET Framework 3.5 為目標，則使用者電腦上需要 .NET Framework 3.5。 在此範例中，如果只有 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 安裝在終端使用者電腦上，您的方案將不會執行。

 2. 在此案例中，只有方案不使用 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 的新功能時，方案才能在 2007 Microsoft Office system 中執行無誤。

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>執行使用 Visual Studio 2010 之前的 Visual Studio 版本所建立的 Office 方案
 Microsoft Office 應用程式可以執行使用 Visual Studio 2010 之前版本的 Visual Studio 所建立的方案。 在某些情況下，這些方案需要不同版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 不同版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可以並存安裝在同一部電腦上。

 下表顯示哪些 Microsoft Office 版本可以執行使用舊版 Visual Studio 所建立的方案，以及 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 每個解決方案需要哪些版本的和 .NET Framework。

|用來建立方案的 Visual Studio 版本|專案範本的目標 Office 版本|可以執行方案的 Office 版本|終端使用者電腦上的必要執行時間|終端使用者電腦上的必要 .NET Framework 版本|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> 或<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 與 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> 2007 Microsoft Office system|適用于 Office Runtime<sup>1</sup>的 Visual Studio 2010 工具<br /><br /> 或<br /><br /> Visual Studio Tools for the Microsoft Office system (3.0 版執行階段)|.NET Framework 3.5|
|已安裝 VSTO 2005 SE<sup>2</sup> 的下列其中一種版本的 Visual Studio 2005：<br /><br /> -Visual Studio 2005 Tools for Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 專業版|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (僅限32位的<sup>3</sup>) <br /><br /> 2007 Microsoft Office system|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5|
|下列任何 Visual Studio 版本：<br /><br /> -Visual Studio 2008 專業版<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools for Office (（含或未安裝 VSTO 2005 SE<sup>2</sup> ）) <br />-Visual Studio Team System 2005 (，不論是否已安裝 VSTO 2005 SE<sup>2</sup>) <br />-已安裝 Visual Studio 2005 Professional with VSTO 2005 SE<sup>2</sup>|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (僅限32位的<sup>3</sup>) <br /><br /> 2007 Microsoft Office system<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 應用程式包含適用于 Office 執行時間的 Visual Studio 2010 工具。 因此，在此案例中，這些應用程式一律會使用適用于 Office 執行時間的 Visual Studio 2010 工具，而不是 Microsoft Office 系統 (3.0 版執行時間) 的 Visual Studio Tools。 2007 Microsoft Office system 中的應用程式可以使用 Visual Studio 2010 Tools for Office Runtime 或 Visual Studio Tools for the Microsoft Office system (3.0 版執行階段)。

 2. VSTO 2005 SE 是免費的 Visual Studio 附加元件，可提供 Microsoft Office 2003 及 2007 Microsoft Office system 的 VSTO 增益集專案範本。 它可以與 Visual Studio 2005 Professional、Visual Studio 2005 Tools for Office 或 Visual Studio Team System 2005 中的版本一起安裝。 如需詳細資訊，請參閱 [Visual Studio 2005 Tools For Office Second Edition](https://developer.microsoft.com/office/docs)。

 3. 需要 Visual Studio 2005 Tools for Office Second Edition Runtime 的 Office 方案與 64 位元版本的 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 不相容。 若要在 64 位元版本的 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 執行這些方案，您必須先將專案升級成 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 或以 2007 Microsoft Office system 為目標的 Visual Studio 2008 專案。

## <a name="see-also"></a>另請參閱
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio Tools for Office 執行時間安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [設定電腦以開發 Office 方案](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
