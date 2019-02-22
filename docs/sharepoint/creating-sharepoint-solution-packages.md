---
title: 建立 SharePoint 方案套件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 147bb56e0d8759ece67ea1454f496b23b770cebf
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604726"
---
# <a name="create-sharepoint-solution-packages"></a>建立 SharePoint 方案套件
  藉由使用 封裝設計工具，您可以建立並自訂部署套件。 例如，您可以新增 SharePoint 專案項目和功能，重設 IIS 伺服器、 設定功能啟用範圍，以及識別功能相依性。 設計工具也會產生資訊清單，描述每個封裝的 XML 檔案。

## <a name="packaging-tools"></a>封裝工具
 您可以使用**封裝設計工具**自訂封裝，並產生資訊清單。 您可以包含 SharePoint 專案項目，設定是否應該重設，以及設定部署伺服器類型的 Web 伺服器。 如需詳細資訊，請參閱[如何：新增與移除功能和封裝的項目使用 Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。

 或者，您可以使用**封裝總管**若要修改的功能和套件檔案中的項目 (*.wsp*)。 如需詳細資訊，請參閱[如何：新增和移除功能和項目加入封裝時，使用 [封裝總管] 中](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

 您可以使用 Visual Studio 和 MSBuild 來建立封裝 (*.wsp*) 來部署 SharePoint 方案的檔案。 此程序會產生所需的 SharePoint 部署資訊清單檔案。 如需詳細資訊，請參閱[如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。

## <a name="package-designer-options"></a>封裝設計工具選項
 下表顯示的屬性，您可以自訂在 SharePoint 封裝**封裝設計工具**。

|封裝設計工具屬性|預設設定的描述|
|-------------------------------|------------------------------------|
|名稱|必要項。 封裝的預設名稱設為*ProjectName*。|
|重設 web 伺服器|選擇性。 如果您想要重新啟動 Web 伺服器之後，請選取 *.wsp*檔案會安裝在 SharePoint 伺服器上。|
|部署伺服器類型|必要項。 根據預設，範圍是設定為 ApplicationServer。<br /><br /> ApplicationServer:描述裝載服務的伺服器。<br /><br /> WebFrontEnd:描述裝載網站的伺服器。|
|在方案中的項目|所有的 SharePoint 專案項目和可以加入至封裝的功能。|
|在封裝中的項目|選擇性。 所有的 SharePoint 項目和您想要部署套件中的功能。|

## <a name="configure-the-packaging-process"></a>設定封裝的程序
 開發 Visual Studio 中的 SharePoint 方案之後，您可以自訂封裝專案的方式。

 下表顯示您可以使用自訂的兩個 MSBuild 目標如何 *.wsp*建立檔案。

|目標|描述|
|------------|-----------------|
|BeforeLayout|目標檔案會複製到中繼目錄之前，立即執行工作。 您可以修改檔案，然後再建立的封裝檔案 (*.wsp*)。|
|AfterLayout|目標檔案會複製到中繼目錄之後，立即執行工作。|

 如需詳細資訊， [How to:使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)。

## <a name="packaging-architecture"></a>封裝架構
 當您建立 SharePoint 套件時，會執行下列步驟 (*.wsp*) 在 Visual Studio 中。

1.  功能和封裝驗證，以確定封裝的實體和語意結構正確無誤。

2.  列舉功能、 專案項目和封裝中的封裝檔案。 封裝和功能的資訊清單檔會轉換為包含部署和啟用的所有必要資訊。 權杖會以完整格式的值取代。

3.  可自訂 BeforeLayout MSBuild 目標會執行。 您可以建立這個步驟會讓封裝之前的任何自訂修改 *.wsp*建立檔案。

4.  列舉的檔案會複製到中繼目錄。

5.  可自訂的 AfterLayout MSBuild 目標會執行。 您可以建立這個步驟會讓封裝之前的任何自訂修改 *.wsp*建立檔案。

6.  中繼目錄內檔案會新增至 *.wsp*檔案。

## <a name="package-folder-structure"></a>套件資料夾結構
 當您封裝 SharePoint 專案中， *.wsp*檔案會為您在建立*SolutionFolder\bin\\\<BuildConfiguration >* 資料夾。 例如，如果您的解決方案處於*C:\Visual Studio 2013 \ projects\listdefinition1*和您的組建組態設為版本中， *.wsp*檔案會位於*C:\Visual Studio 2013\Projects\ListDefinition1\bin\Release*。

## <a name="see-also"></a>另請參閱
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：新增和移除功能和項目加入封裝時，使用封裝設計工具](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
