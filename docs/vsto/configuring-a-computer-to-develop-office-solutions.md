---
title: "設定電腦以開發 Office 方案 |Microsoft 文件"
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
helpviewer_keywords: Office development in Visual Studio, installing tools
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: "97"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d3e0b354375d6116a1bcc0cc2b0d69ecc2f16b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>設定電腦以開發 Office 方案
  若要為 Microsoft Office 建立 VSTO 增益集和自訂，請安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本。  
  
|軟體|支援的版本|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**重要事項：**您必須在安裝期間選取 [Microsoft Office Developer Tools] 核取方塊。|  
|.NET Framework|-.NET Framework 4 或更新版本。|  
|Microsoft Office|<ul><li>任何 Office 套件版本，包括 Office Professional Plus for Office 365。</li><li>下列任何一種獨立應用程式：<br /><br /> <ul><li>Excel</li><li>InfoPath (僅限 Office 2013 和 Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> 必須在安裝 Office 時安裝 Visual Basic for Applications (VBA)。 **重要事項：**按一下執行版本的 Office 2010 應用程式不支援。|  
  
 如需詳細的安裝步驟，請參閱[How to： 設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>如果未顯示專案範本，或無法在 Visual Studio  
 如果您安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本，但 Office 專案範本未顯示在 Visual Studio**新專案**對話方塊中，或您收到錯誤時要使用其中一個，再試一次請檢查下列項目：  
  
-   確定電腦上已安裝 Microsoft Office 開發人員工具。  
  
     Office 開發人員工具是 Visual Studio 的選用元件，但通常會隨著 Visual Studio 自動安裝。 如果您透過指定要安裝的功能來自訂 Visual Studio 安裝，請確定已在安裝期間選擇 [Microsoft Office Developer Tools]  ，以安裝這些工具。  
  
     若要確定是否已安裝這些工具，請啟動 Visual Studio 安裝程式，並選擇 [修改]  按鈕。 選取 [Microsoft Office Developer Tools]  核取方塊，然後選擇 [更新]  按鈕。  
  
-   請確定您執行的 Office 版本不是隨選即用版本。 請參閱 [如何：驗證電腦上的 Outlook 是否為隨選即用應用程式](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx)。  
  
-   請確定您執行只有一個版本的 Microsoft Office。  
  
 如果持續發生問題，請參閱 [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)   
 [如何： 設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何： 安裝 Visual Studio Tools for Office Runtime 可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [如何： 安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)  
  
  