---
title: "執行不同版本的 Microsoft Office 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a52ab5c2f2f5a367681929966175ca4c4cb33b56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>在不同的 Microsoft Office 版本中執行方案
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>執行使用 Visual Studio 2010 和更新版本建立的 Office 方案  
  
|專案範本的目標 Office 版本|專案的目標.NET Framework<sup>1</sup>|可以執行方案的 Office 版本|在使用者電腦上的必要執行階段|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 和 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] (含) 以後版本|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] (含) 以後版本|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|2007 Microsoft Office system|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] (含) 以後版本<br /><br /> 或<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime|  
  
 1. 終端使用者電腦上必須有您專案的目標 .NET Framework 版本，您的方案才能執行。 例如，如果您專案的目標為 .NET Framework 3.5，則在使用者電腦上必須有 .NET Framework 3.5。 在此範例中，如果在使用者電腦上只有安裝 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，則無法執行您的方案。  
  
 2. 在此案例中，只有方案不使用 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 的新功能時，方案才能在 2007 Microsoft Office system 中執行無誤。  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>執行使用 Visual Studio 2010 之前版本的 Visual Studio 所建立的 Office 方案  
 Microsoft Office 應用程式可以執行使用 Visual Studio 2010 之前版本的 Visual Studio 所建立的方案。 在某些情況下，這些方案需要不同版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 不同版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可以並存安裝在同一部電腦上。  
  
 下表顯示哪些版本的 Microsoft Office 可以執行使用舊版 Visual Studio 中，建立方案和哪些版本[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]和.NET Framework 所需的每個解決方案。  
  
|用來建立方案的 Visual Studio 版本|專案範本的目標 Office 版本|可以執行方案的 Office 版本|在終端使用者電腦上的必要執行階段|在使用者電腦上的必要 .NET Framework 版本|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> 或<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]和[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 Microsoft Office system|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> 或<br /><br /> Visual Studio Tools for the Microsoft Office system (3.0 版執行階段)|.NET Framework 3.5|  
|其中一個下列版本的 Visual Studio 2005 VSTO 2005 se<sup>2</sup>安裝：<br /><br /> -Visual Studio 2005 Tools for Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office system|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]和[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)](僅限 32 位元<sup>3</sup>)<br /><br /> 2007 Microsoft Office system|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5|  
|下列任何 Visual Studio 版本：<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools for Office (VSTO 2005 SE 含<sup>2</sup>安裝)<br />-Visual Studio Team System 2005 (含 VSTO 2005 SE<sup>2</sup>安裝)<br />-Visual Studio 2005 Professional VSTO 2005 se<sup>2</sup>安裝|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]和[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)](僅限 32 位元<sup>3</sup>)<br /><br /> 2007 Microsoft Office system<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2.0、.NET Framework 3.0 或 .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 應用程式包含 Visual Studio 2010 Tools for Office Runtime。 因此，在此案例中這些應用程式一律使用 Visual Studio 2010 Tools for Office Runtime，而不是 Visual Studio Tools for the Microsoft Office system (3.0 版執行階段)。 2007 Microsoft Office system 中的應用程式可以使用 Visual Studio 2010 Tools for Office Runtime 或 Visual Studio Tools for the Microsoft Office system (3.0 版執行階段)。  
  
 2. VSTO 2005 SE 是免費的 Visual Studio 附加元件，可提供 Microsoft Office 2003 及 2007 Microsoft Office system 的 VSTO 增益集專案範本。 它可以與 Visual Studio 2005 Professional、Visual Studio 2005 Tools for Office 或 Visual Studio Team System 2005 中的版本一起安裝。 如需詳細資訊，請參閱[Visual Studio 2005 Tools for Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446)。  
  
 3. 需要 Visual Studio 2005 Tools for Office Second Edition Runtime 的 Office 方案與 64 位元版本的 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 不相容。 若要在 64 位元版本的 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 執行這些方案，您必須先將專案升級成 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 或以 2007 Microsoft Office system 為目標的 Visual Studio 2008 專案。  
  
## <a name="see-also"></a>請參閱  
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [設定電腦以開發 Office 方案](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  