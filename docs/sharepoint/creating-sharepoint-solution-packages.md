---
title: 建立 SharePoint 方案套件 |Microsoft Docs
description: 使用封裝設計工具建立和自訂 SharePoint 方案的部署套件。 探索封裝工具、設計工具選項和資料夾結構。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 423fcaf54d1d46ddf92352f4ff8bdbb637bbe514
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949086"
---
# <a name="create-sharepoint-solution-packages"></a>建立 SharePoint 方案套件
  您可以使用封裝設計工具來建立和自訂部署套件。 例如，您可以加入 SharePoint 專案專案和功能、重設 IIS 伺服器、設定功能啟用範圍，以及識別功能相依性。 設計工具也會產生資訊清單，這是描述每個封裝的 XML 檔。

## <a name="packaging-tools"></a>封裝工具
 您可以使用 **封裝設計** 工具來自訂封裝並產生資訊清單。 您可以包含 SharePoint 專案專案、設定是否要重設 Web 服務器，以及設定部署伺服器類型。 如需詳細資訊，請參閱 [如何：使用封裝設計工具加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。

 或者，您也可以使用 **封裝瀏覽器** 來修改封裝檔中的功能和專案， (*.wsp*) 。 如需詳細資訊，請參閱 [如何：使用封裝瀏覽器加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

 您可以使用 Visual Studio 和 MSBuild 來建立封裝 (*.wsp*) 檔，以部署 SharePoint 方案。 此進程會產生 SharePoint 部署所需的資訊清單檔案。 如需詳細資訊，請參閱 [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)。

## <a name="package-designer-options"></a>封裝設計工具選項
 下表顯示您可以使用 **封裝設計** 工具在 SharePoint 封裝中自訂的屬性。

|封裝設計工具屬性|預設設定的描述|
|-------------------------------|------------------------------------|
|名稱|必要。 封裝的預設名稱會設定為 [ *專案* 名稱]。|
|重設 Web 服務器|選擇性。 如果您要在 SharePoint 伺服器上安裝 *.wsp* 檔案之後，重新開機 Web 服務器，請選取此項。|
|部署伺服器類型|選擇性。 代表主控封裝的伺服器類型。 如果未設定，則預設為 WebFrontEnd。<br /><br /> ApplicationServer：描述裝載服務的伺服器。<br /><br /> WebFrontEnd：描述主控網站的伺服器。|
|方案中的專案|所有可以新增至封裝的 SharePoint 專案專案和功能。|
|封裝中的專案|選擇性。 您要在封裝中部署的所有 SharePoint 專案和功能。|

## <a name="configure-the-packaging-process"></a>設定封裝進程
 在 Visual Studio 中開發 SharePoint 方案之後，您就可以自訂封裝專案的方式。

 下表顯示兩個您可以用來自訂 *.wsp* 檔案建立方式的 MSBuild 目標。

|目標|Description|
|------------|-----------------|
|BeforeLayout|在檔案複製到中繼目錄前立即執行工作的目標。 您可以在建立封裝檔 (*.wsp*) 之前修改檔案。|
|AfterLayout|將檔案複製到中繼目錄後立即執行工作的目標。|

 如需詳細資訊，請 [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)。

## <a name="packaging-architecture"></a>封裝架構
 當您在 Visual Studio 中建立 (*.wsp*) 的 SharePoint 套件時，會發生下列步驟。

1. 系統會驗證功能和套件，以確保封裝的實體和語義結構正確無誤。

2. 列舉套件中的功能、專案專案和封裝檔案。 封裝和功能的資訊清單檔會轉換成包含部署和啟用的所有必要資訊。 這些標記會以完整值取代。

3. 執行可自訂的 BeforeLayout MSBuild 目標。 您可以建立此步驟，以在建立 *.wsp* 檔案之前對封裝進行任何自訂修改。

4. 列舉的檔案會複製到中繼目錄。

5. 執行可自訂的 AfterLayout MSBuild 目標。 您可以建立此步驟，以在建立 *.wsp* 檔案之前對封裝進行任何自訂修改。

6. 中繼目錄中的檔案會新增至 *.wsp* 檔案。

## <a name="package-folder-structure"></a>套件資料夾結構
 當您封裝 SharePoint 專案時，會在 *SolutionFolder\bin \\ \<BuildConfiguration>* 資料夾中為您建立 *.wsp* 檔。 例如，如果您的方案是在 *C:\Visual Studio 2013 \ Projects\ListDefinition1* 中，而組建設定設為 [發行]，則 *.Wsp* 檔案位於 *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*。

## <a name="see-also"></a>另請參閱
- [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [如何：使用封裝設計工具加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 工作建立 SharePoint 方案套件](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [如何：使用 MSBuild 目標自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
