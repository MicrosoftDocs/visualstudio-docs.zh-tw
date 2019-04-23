---
title: 封裝和部署 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c187865518c9556d63d9e5e632ec5c658fc3e0f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040840"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>封裝和部署 SharePoint 方案
  一般而言，SharePoint 解決方案會使用方案套件 (.wsp) 檔案部署到 SharePoint 伺服器。 若要將您的 SharePoint 專案項目組織成功能，並建立要部署您的 SharePoint 功能的套件，您可以使用 Visual Studio。

 本主題提供下列資訊：

- [建立功能和封裝](#create-features-and-packages)

- [功能和封裝工具支援](#feature-and-packaging-tool-support)

- [部署 SharePoint 方案](#deploy-sharepoint-solutions)

- [部署 SharePoint 方案中的檔案](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>建立功能和封裝
 您可以使用 Visual Studio 來分組到相關的 SharePoint 項目*功能*。 比方說，在連絡人清單定義一項功能可能包括清單執行個體和清單定義。 您可以將這兩個元素合併成單一的功能進行部署。 如需有關功能的詳細資訊，請參閱[建置組塊：功能](http://go.microsoft.com/fwlink/?LinkID=169183)。

 接下來，您可以在其中建立 SharePoint 方案套件 (*.wsp*) 套件組合的多項功能，網站定義、 組件和其他檔案至單一套件，將檔案儲存在 SharePoint 部署的檔案所需的格式在伺服器中。 如需詳細資訊，請參閱[建置組塊：解決方案](http://go.microsoft.com/fwlink/?LinkID=169186)。

## <a name="feature-and-packaging-tool-support"></a>功能和封裝工具支援
 您可以使用 Visual Studio 中的 SharePoint 開發工具，快速將您的 SharePoint 檔案組織成功能和更容易部署的方案套件。 若要設定的功能和方案套件，您可以使用下列工具。

- 功能設計工具和封裝設計工具。

- 封裝總管 中，工具視窗。

- 方案總管 中。

### <a name="feature-designer-and-package-designer"></a>功能設計工具] 和 [封裝設計工具
 您可以建立功能、 設定範圍，並標示為相依性的其他功能，使用功能設計工具。 設計工具也會顯示描述每項功能的最終 XML 檔案。 如需詳細資訊，請參閱 <<c0> [ 建立的 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。

 套用至特定網站或網站群組的功能，藉由設定其*範圍*功能設計工具中。 如果個別的網站啟動功能，此功能僅適用於該特定網站。 如果網站集合啟用功能，此功能中的項目套用至整個網站集合。 如需詳細資訊，請參閱 <<c0> [ 項目範圍](http://go.microsoft.com/fwlink/?LinkID=169189)。

 如果您的功能會依賴其他功能，您可以設定*功能啟用相依性*來進行您的功能可用之前，先標示相依的功能。 功能啟用相依性檢查相依的功能都已經在該範圍中啟動。 如需詳細資訊，請參閱 <<c0> [ 啟用相依性和範圍](http://go.microsoft.com/fwlink/?LinkID=169190)。

 在封裝設計工具中，您可以 SharePoint 項目分組到單一方案套件，以及設定是否要在部署期間重設 Web 伺服器。 若要設定部署伺服器類型，使用**屬性**視窗。 設計工具也會產生描述套件內容的 XML 檔案。 如需詳細資訊，請參閱 <<c0> [ 建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。

 在部署期間，Internet Information Services (IIS) 服務已停止，將方案檔複製到 SharePoint 伺服器。 在 Visual Studio 中使用封裝設計工具，您可以選取是否應重新啟動 Web 伺服器。 若要設定前端網頁伺服器或應用程式伺服器部署方案時，請使用**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 方案項目 （方案）](http://go.microsoft.com/fwlink/?LinkID=169191)。

### <a name="packaging-explorer"></a>封裝總管
 若要補充的功能設計工具和封裝設計工具，您可以使用 [封裝總管] 中，將 SharePoint 檔案分組到功能和封裝。 此外，您可以在這裡看到封裝功能，SharePoint 專案的階層式檢視項目和檔案。 [封裝總管] 是工具視窗可供您完成下列工作：

- 開啟 SharePoint 專案項目和檔案。

- 拖放的一項功能的 SharePoint 專案項目到另一個。

- 拖放 SharePoint 專案項目和功能從某個封裝到另一個。

- 將新的功能加入封裝。

- 開啟功能或封裝的設計工具。

- 驗證功能和封裝。

  在 Visual Studio 中的 SharePoint 開發工具有驗證規則，以協助確保方案套件正確。 此外，規則確認 *.wsp*方案檔案已成功部署，並將 SharePoint 伺服器上啟動。 如需 XML 結構描述的功能，請參閱[功能結構描述](http://go.microsoft.com/fwlink/?LinkID=169192)。

  您可以將自訂功能和封裝驗證規則新增至 SharePoint 專案系統。 如需詳細資訊，請參閱[如何：建立自訂的功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。

  如需 [封裝總管] 中的詳細資訊，請參閱[How to:新增和移除功能和項目加入封裝時，使用 [封裝總管] 中](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

### <a name="solution-explorer"></a>底下提供說明，包括方案總管
 您可以使用 [方案總管] 來瀏覽並開啟 SharePoint 專案的檔案。 在 [方案總管] 中使用操作功能表，以加入功能，功能事件接收器，和功能的資源。 此外，您可以開啟功能設計工具與封裝設計工具，來設定部署套件的功能。

## <a name="deploy-sharepoint-solutions"></a>部署 SharePoint 方案
 在自訂的功能和 Visual Studio 中的封裝之後，您可以建立 *.wsp*檔案部署至 SharePoint 伺服器。 您可以使用 Visual Studio 偵錯及測試。*wsp*只在開發電腦上的 SharePoint 伺服器上。 如需如何將 SharePoint 方案部署至遠端 SharePoint 伺服器的詳細資訊，請參閱[部署解決方案](http://go.microsoft.com/fwlink/?LinkID=169194)。

 您也可以自訂部署步驟，在開發電腦上。 如需詳細資訊，請參閱 <<c0> [ 部署、 發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。

## <a name="deploy-files-in-sharepoint-solutions"></a>部署 SharePoint 方案中的檔案
 一般而言，當您將 SharePoint 專案項目加入 SharePoint 方案時，所有必要的檔案會包含。 編譯 （程式碼檔案） 的檔案，可以是內建解決方案的輸出組件。 不過，您也可以加入非可編譯檔案，例如 *.xml*， *.txt*，或加入 SharePoint 專案的資源檔。 這些檔案不會自動封裝在您的解決方案。 若要確保它們會封裝，請將檔案新增至對應的資料夾或 SharePoint 專案項目。

 部署方案時，會自動新增到對應的資料夾的檔案複製到 SharePoint 登錄區。 檔案新增至 SharePoint 專案項目都部署到在指定的位置**部署位置**每個檔案，這部分設定的屬性，根據**部署類型**屬性。 根據預設，**部署類型**屬性值是**NoDeployment**，這表示不會隨著方案部署的檔案。 您必須設定為包含在封裝中的檔案屬性的另一個值。

 例如，若要新增 *.xml*檔案至 SharePoint 專案中，執行下列動作之一：

- 專案中加入 SharePoint"版面配置 」 對應資料夾。 這會在建立**方案總管**名為的資料夾**版面配置**具有專案子資料夾。 新增 *.xml*到新的子資料夾。 根據預設，檔案會部署到 SharePoint 檔案系統下 *...\TEMPLATE\LAYOUTS\\\<資料夾名稱 >*。 如需如何新增對應的資料夾資訊，請參閱[如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

- 新增 *.xml*檔案的 SharePoint 專案項目中，資料夾，然後變更**部署類型**屬性 *.xml*檔案從**NoDeployment**另一個設定這類**RootFile**或是**ElementFile**。 適當**部署類型**設定取決於檔案和專案。 如需詳細資訊**部署類型**屬性設定，請參閱[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。

  如果加入的檔案不適用於方案中任何特定專案中，您可以將空白的 SharePoint 專案新增至您的解決方案，並再將其他檔案新增至它。 針對至內容資料庫，特別是將檔案部署至 SharePoint，另一個替代方式是將模組新增至專案，然後將檔案新增至模組。 如需詳細資訊，請參閱 <<c0> [ 使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
