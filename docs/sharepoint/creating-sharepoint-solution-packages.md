---
title: "建立 SharePoint 方案套件 |Microsoft 文件"
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
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
ms.assetid: 6b1f1fbf-fa9c-453d-80af-36ec9829677a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f21356c34a94540d20be2bb9fa092bff270f1a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-solution-packages"></a>建立 SharePoint 方案套件
  使用封裝設計工具，您可以建立並自訂部署套件。 例如，您可以加入 SharePoint 專案項目和功能，重設 IIS 伺服器、 設定功能啟動範圍，以及識別功能依存性。 在設計工具也會產生資訊清單描述每個封裝的 XML 檔案。  
  
## <a name="packaging-tools"></a>封裝工具  
 您可以使用**封裝設計工具**自訂封裝，並產生資訊清單。 您可以加入 SharePoint 專案項目，設定是否應該重設，以及設定部署伺服器類型的 Web 伺服器。 如需詳細資訊，請參閱[如何： 加入和移除使用封裝設計工具的功能和封裝的項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。  
  
 或者，您可以使用**封裝總管**來修改項目在封裝檔案 (.wsp) 的功能。 如需詳細資訊，請參閱[如何： 新增與移除功能和封裝的項目使用封裝總管](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
 您可以使用 Visual Studio 和 MSBuild 以建立部署 SharePoint 方案套件 (.wsp) 檔案。 此程序會產生所需的 SharePoint 部署資訊清單檔案。 如需詳細資訊，請參閱[How to： 建立 SharePoint 套件](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)和[How to： 建立 SharePoint 方案套件使用 MSBuild 工作](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。  
  
## <a name="package-designer-options"></a>封裝設計工具選項  
 下表顯示的屬性，您可以自訂 SharePoint 套件與**封裝設計工具**。  
  
|封裝設計工具屬性|預設設定的說明|  
|-------------------------------|------------------------------------|  
|名稱|必要項。 設定封裝的預設名稱為*ProjectName*。|  
|重設網頁伺服器|選擇項。 如果您想要重新啟動 Web 伺服器，SharePoint 伺服器上安裝.wsp 檔案之後，請選取。|  
|部署伺服器類型|必要項。 根據預設，會將範圍設定為 ApplicationServer。<br /><br /> ApplicationServer： 描述裝載服務的伺服器。<br /><br /> WebFrontEnd： 描述裝載網站的伺服器。|  
|在方案中的項目|所有的 SharePoint 專案項目，可以加入至封裝的功能。|  
|在封裝中的項目|選擇項。 所有的 SharePoint 項目和您想要部署封裝中的功能。|  
  
## <a name="configuring-the-packaging-process"></a>設定封裝的程序  
 開發 Visual Studio 中的 SharePoint 方案之後，您可以自訂封裝專案的方式。  
  
 下表顯示可用於自訂.wsp 檔案的建立方式的兩個 MSBuild 目標。  
  
|目標|描述|  
|------------|-----------------|  
|BeforeLayout|目標，檔案會複製到中繼目錄之前執行的工作。 建立封裝檔案 (.wsp) 之前，您可以修改檔案。|  
|AfterLayout|目標，檔案會複製到中繼目錄後立即執行的工作。|  
  
 如需詳細資訊， [How to： 自訂 SharePoint 方案套件所使用的 MSBuild 目標](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)。  
  
## <a name="packaging-architecture"></a>封裝架構  
 當您在 Visual Studio 中建立 SharePoint 套件 (.wsp)，就會執行下列步驟。  
  
1.  功能和封裝驗證，以確定封裝的實體和語意結構正確無誤。  
  
2.  會列舉功能、 專案項目和套件中的封裝檔案。 轉換的套件及功能的資訊清單檔案以包含部署和啟用的所有必要資訊。 語彙基元所取代完整的值。  
  
3.  執行自訂 BeforeLayout MSBuild 目標。 您可以建立這個步驟，才能進行任何自訂的修改封裝之前.wsp 檔隨即建立。  
  
4.  列舉的檔案會複製到中繼目錄。  
  
5.  可自訂的 AfterLayout MSBuild 目標，會執行。 您可以建立這個步驟，才能進行任何自訂的修改封裝之前.wsp 檔隨即建立。  
  
6.  中繼目錄中的檔案會加入至.wsp 檔案。  
  
## <a name="package-folder-structure"></a>封裝的資料夾結構  
 當您封裝您的 SharePoint 專案時，.wsp 檔案會為您建立在 SolutionFolder\bin\\*BuildConfiguration*資料夾。 例如，如果您的方案處於*磁碟機*: \Visual Studio 2013\Projects\ListDefinition1 和組建組態設為 發行、.wsp 檔案位於*磁碟機*: \Visual Studio 2013 \Projects\ListDefinition1\bin\Release。  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [如何： 新增與移除功能和封裝的項目使用封裝設計工具](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [如何： 建立 SharePoint 套件](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [如何： 使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  