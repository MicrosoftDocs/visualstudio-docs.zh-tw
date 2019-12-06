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
ms.openlocfilehash: b250be3b61cdfc524f049f952f0cf7e65f1c295a
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "74876060"
---
# <a name="create-sharepoint-solution-packages"></a>建立 SharePoint 方案套件
  藉由使用封裝設計工具，您可以建立和自訂部署封裝。 例如，您可以新增 SharePoint 專案專案和功能、重設 IIS 伺服器、設定功能啟用範圍，以及識別功能相關性。 設計工具也會產生資訊清單，這是描述每個封裝的 XML 檔案。

## <a name="packaging-tools"></a>封裝工具
 您可以使用**封裝設計**工具來自訂封裝並產生資訊清單。 您可以包含 SharePoint 專案專案、設定是否應重設網頁伺服器，以及設定部署伺服器類型。 如需詳細資訊，請參閱[如何：使用封裝設計工具加入和移除封裝中的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。

 或者，您可以使用 [**封裝瀏覽器**] 來修改封裝檔案（ *.wsp*）中的功能和專案。 如需詳細資訊，請參閱[如何：使用封裝瀏覽器新增和移除封裝中的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

 您可以使用 Visual Studio 和 MSBuild 來建立封裝（ *.wsp*）檔案，以部署 SharePoint 方案。 此程式會產生 SharePoint 部署所需的資訊清單檔案。 如需詳細資訊，請參閱[如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。

## <a name="package-designer-options"></a>封裝設計工具選項
 下表顯示您可以使用**封裝設計**工具在 SharePoint 封裝中自訂的屬性。

|封裝設計工具屬性|預設設定的描述|
|-------------------------------|------------------------------------|
|Name|必要項。 封裝的預設名稱會設定為*專案*名稱。|
|重設 Web 服務器|選擇項。 如果您想要在 SharePoint 伺服器上安裝 *.wsp*檔案之後重新開機 Web 服務器，請選取此檔案。|
|部署伺服器類型|選擇項。 代表裝載封裝的伺服器類型。 如果未設定，則會預設為 WebFrontEnd。<br /><br /> ApplicationServer：描述裝載服務的伺服器。<br /><br /> WebFrontEnd：描述裝載網站的伺服器。|
|方案中的專案|所有可新增至封裝的 SharePoint 專案專案和功能。|
|封裝中的專案|選擇項。 您想要在封裝中部署的所有 SharePoint 專案和功能。|

## <a name="configure-the-packaging-process"></a>設定封裝程式
 在 Visual Studio 中開發 SharePoint 方案之後，您可以自訂封裝專案的方式。

 下表顯示兩個 MSBuild 目標，您可以用來自訂建立 *.wsp*檔案的方式。

|Target|描述|
|------------|-----------------|
|BeforeLayout|在檔案複製到中繼目錄之前，立即執行工作的目標。 您可以在建立封裝檔案（ *.wsp*）之前修改檔案。|
|AfterLayout|在檔案複製到中繼目錄後立即執行工作的目標。|

 如需詳細資訊，請瞭解[如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)。

## <a name="packaging-architecture"></a>封裝架構
 當您在 Visual Studio 中建立 SharePoint 封裝（ *.wsp*）時，會發生下列步驟。

1. 系統會驗證這些功能和套件，以確定封裝的實體和語義結構是正確的。

2. 系統會列舉封裝中的功能、專案專案和封裝檔案。 封裝和功能的資訊清單檔案會進行轉換，以包含部署和啟用的所有必要資訊。 標記會取代為完整的值。

3. 會執行可自訂的 BeforeLayout MSBuild 目標。 建立 *.wsp*檔案之前，您可以建立此步驟來對封裝進行任何自訂修改。

4. 列舉的檔案會複製到中繼目錄。

5. 會執行可自訂的 AfterLayout MSBuild 目標。 建立 *.wsp*檔案之前，您可以建立此步驟來對封裝進行任何自訂修改。

6. 中繼目錄中的檔案會加入至 *.wsp*檔案。

## <a name="package-folder-structure"></a>套件資料夾結構
 當您封裝 SharePoint 專案時，會在*SolutionFolder\bin\\\<BuildConfiguration >* 資料夾中為您建立 *.wsp*檔案。 例如，如果您的解決方案是在*C:\Visual Studio 2013 \ Projects\ListDefinition1*中，而您的組建設定設為 [發行]，則 *.Wsp*檔案位於*C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*中。

## <a name="see-also"></a>請參閱
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：使用封裝設計工具在封裝中加入和移除功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
