---
title: 建立 SharePoint 方案套件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 957789c4adfc476429179ed84f87f544c0d37143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765267"
---
# <a name="create-sharepoint-solution-packages"></a>建立 SharePoint 方案套件
  使用封裝設計工具，您可以建立並自訂部署套件。 例如，您可以加入 SharePoint 專案項目和功能，重設 IIS 伺服器、 設定功能啟動範圍，以及識別功能依存性。 在設計工具也會產生資訊清單描述每個封裝的 XML 檔案。  
  
## <a name="packaging-tools"></a>封裝工具
 您可以使用**封裝設計工具**自訂封裝，並產生資訊清單。 您可以加入 SharePoint 專案項目，設定是否應該重設，以及設定部署伺服器類型的 Web 伺服器。 如需詳細資訊，請參閱[如何： 加入和移除使用封裝設計工具的功能和封裝的項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。  
  
 或者，您可以使用**封裝總管**修改的功能和封裝檔案中的項目 (*.wsp*)。 如需詳細資訊，請參閱[如何： 新增與移除功能和封裝的項目使用封裝總管](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
 您可以使用 Visual Studio 和 MSBuild 來建立封裝 (*.wsp*) 部署 SharePoint 方案檔。 此程序會產生所需的 SharePoint 部署資訊清單檔案。 如需詳細資訊，請參閱[How to： 建立 SharePoint 套件](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)和[How to： 建立 SharePoint 方案套件使用 MSBuild 工作](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。  
  
## <a name="package-designer-options"></a>封裝設計工具選項
 下表顯示的屬性，您可以自訂 SharePoint 套件與**封裝設計工具**。  
  
|封裝設計工具屬性|預設設定的說明|  
|-------------------------------|------------------------------------|  
|名稱|必要。 設定封裝的預設名稱為*ProjectName*。|  
|重設網頁伺服器|選擇性。 如果您想要重新啟動 Web 伺服器之後，請選取 *.wsp*檔案會安裝在 SharePoint 伺服器上。|  
|部署伺服器類型|必要。 根據預設，會將範圍設定為 ApplicationServer。<br /><br /> ApplicationServer： 描述裝載服務的伺服器。<br /><br /> WebFrontEnd： 描述裝載網站的伺服器。|  
|在方案中的項目|所有的 SharePoint 專案項目，可以加入至封裝的功能。|  
|在封裝中的項目|選擇性。 所有的 SharePoint 項目和您想要部署封裝中的功能。|  
  
## <a name="configure-the-packaging-process"></a>設定封裝的程序
 開發 Visual Studio 中的 SharePoint 方案之後，您可以自訂封裝專案的方式。  
  
 下表顯示兩個 MSBuild 目標，您可以用來自訂如何 *.wsp*建立檔案。  
  
|目標|描述|  
|------------|-----------------|  
|BeforeLayout|目標，檔案會複製到中繼目錄之前執行的工作。 您可以修改之前建立封裝檔案的檔案 (*.wsp*)。|  
|AfterLayout|目標，檔案會複製到中繼目錄後立即執行的工作。|  
  
 如需詳細資訊， [How to： 自訂 SharePoint 方案套件所使用的 MSBuild 目標](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)。  
  
## <a name="packaging-architecture"></a>封裝架構
 當您建立 SharePoint 套件時，會發生下列步驟 (*.wsp*) 在 Visual Studio 中。  
  
1.  功能和封裝驗證，以確定封裝的實體和語意結構正確無誤。  
  
2.  會列舉功能、 專案項目和套件中的封裝檔案。 轉換的套件及功能的資訊清單檔案以包含部署和啟用的所有必要資訊。 語彙基元所取代完整的值。  
  
3.  執行自訂 BeforeLayout MSBuild 目標。 您可以建立這個步驟，讓封裝之前的任何自訂修改 *.wsp*建立檔案。  
  
4.  列舉的檔案會複製到中繼目錄。  
  
5.  可自訂的 AfterLayout MSBuild 目標，會執行。 您可以建立這個步驟，讓封裝之前的任何自訂修改 *.wsp*建立檔案。  
  
6.  中繼目錄內檔案會新增至 *.wsp*檔案。  
  
## <a name="package-folder-structure"></a>套件資料夾結構
 當您封裝您的 SharePoint 專案 *.wsp*檔案會為您在建立*SolutionFolder\bin\{BuildConfiguration}* 資料夾。 例如，如果您的方案處於*C:\Visual Studio 2013\Projects\ListDefinition1*和組建組態設為發行， *.wsp*檔案位於*C:\Visual Studio 2013 \Projects\ListDefinition1\bin\Release*。  
  
## <a name="see-also"></a>另請參閱
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [如何： 新增與移除功能和封裝的項目使用封裝設計工具](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [如何： 建立 SharePoint 套件](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [如何： 使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 