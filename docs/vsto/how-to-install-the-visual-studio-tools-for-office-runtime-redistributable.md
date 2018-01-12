---
title: "如何： 安裝 Visual Studio Tools for Office Runtime 可轉散發套件 |Microsoft 文件"
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
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f76191ca8b41f252e5009c0d3e7e09415f6f081
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>如何：安裝 Visual Studio Tools for Office Runtime 可轉散發套件
  執行使用中的 Microsoft Office developer tools 建立的方案，每一部電腦上必須安裝 Visual Studio 2010 Tools for Office Runtime [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 當您安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 Microsoft Office 時，此執行階段會自動安裝。 如需詳細資訊，請參閱 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
 在下列情況下，您可能需要遵循手動安裝指示：  
  
-   您需要在伺服器上安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，您想要使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別管理伺服器上的文件層級方案。  
  
-   您需要在已安裝所有其他 Office 方案必要條件的電腦上安裝執行階段。  
  
    > [!NOTE]  
    >  您必須是開發電腦上的系統管理員，才能安裝 .NET Framework 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>安裝 Visual Studio Tools for Office Runtime  
  
1.  請安裝 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本。  
  
    -   若要下載[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，請參閱[Microsoft.NET Framework 4 （Web 安裝程式）](http://go.microsoft.com/fwlink/?LinkId=178957)。  
  
    -   若要下載[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]，請參閱[Microsoft.NET Framework 4 Client Profile （Web 安裝程式）](http://go.microsoft.com/fwlink/?LinkId=178958)。  
  
    -   若要下載[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，請參閱[Microsoft.NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)。  
  
2.  執行 vstor_redist.exe 以安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
     您可以下載這些安裝程式檔案從[Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384)。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的必要條件符合 .NET Framework 的必要條件。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]包含語言套件。 如果您的 Windows 安裝設定為英文以外的語言，您可以使用在 Windows 上的相同語言顯示執行階段訊息。 同樣地，如果使用者安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，然後在安裝設定為英文以外之語言的 Windows 上執行您的方案，則執行階段訊息會以和 Windows 使用的相同語言顯示。 在某些情況下，您可能需要額外的語言套件。 例如，您可能需要其他語言套件，如果您的 Windows 版本會使用一個以上的語言設定，或在安裝後，您切換到另一種語言[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 您可以找到語言套件時[Microsoft Visual Studio 2010 Tools for Microsoft Office System (4.0 版 Runtime) 語言套件](http://go.microsoft.com/fwlink/?LinkId=140386)。  
  
## <a name="see-also"></a>請參閱  
 [開始使用 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [如何： 設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何： 安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  