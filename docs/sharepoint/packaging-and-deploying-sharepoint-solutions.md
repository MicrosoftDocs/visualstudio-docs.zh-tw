---
title: 封裝和部署 SharePoint 方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 9a4bf3394cf47b4f355fbe6a330ff5374e2da1c9
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015599"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>封裝和部署 SharePoint 方案
  一般來說，SharePoint 方案會使用方案套件（.wsp）檔案部署到 SharePoint 伺服器。 您可以使用 Visual Studio 將 SharePoint 專案專案組織成功能，並建立封裝來部署 SharePoint 功能。

 此主題提供下列資訊：

- [建立功能和套件](#create-features-and-packages)

- [功能與封裝工具支援](#feature-and-packaging-tool-support)

- [部署 SharePoint 方案](#deploy-sharepoint-solutions)

- [在 SharePoint 方案中部署檔案](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>建立功能和套件
 您可以使用 Visual Studio 將相關的 SharePoint 專案組成一個*功能*。 例如，連絡人清單定義的功能可能包含清單實例和清單定義。 您可以將這兩個元素結合成單一功能，以供部署之用。 如需功能的詳細資訊，請參閱[建立區塊：功能](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))。

 接下來，您可以建立 SharePoint 方案套件（*.wsp*），將多個功能、網站定義、元件和其他檔案組合成單一封裝，將檔案儲存成 SharePoint 所需的格式，以將檔案部署至伺服器。 如需詳細資訊，請參閱[建立區塊：解決方案](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14))。

## <a name="feature-and-packaging-tool-support"></a>功能與封裝工具支援
 您可以使用 Visual Studio 中的 SharePoint 開發工具，快速地將 SharePoint 檔案組織成功能和方案套件，以方便部署。 您可以使用下列工具來設定功能和方案套件。

- 功能設計工具和封裝設計工具。

- 封裝 Explorer，這是一個工具視窗。

- 方案總管。

### <a name="feature-designer-and-package-designer"></a>功能設計工具和封裝設計工具
 您可以使用 [功能設計工具] 來建立功能、設定範圍，並將其他功能標記為相依性。 設計工具也會顯示描述每項功能的最終 XML 檔案。 如需詳細資訊，請參閱[建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。

 藉由在 [功能設計工具] 中設定其*範圍*，將功能套用至特定網站或網站群組。 如果已針對個別網站啟動功能，此功能僅適用于該特定網站。 如果已啟用網站集合的功能，則功能中的專案會套用至整個網站集合。 如需詳細資訊，請參閱[元素範圍](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14))。

 如果您的功能相依于其他功能，您可以設定*功能啟用*相依性，以在您的功能可供使用之前，標示相依的功能。 功能啟用相依性會檢查是否已在該範圍啟動相依的功能。 如需詳細資訊，請參閱啟用相依性[和範圍](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14))。

 在封裝設計工具中，您可以將 SharePoint 元素組成單一方案封裝，並設定是否要在部署期間重設 Web 服務器。 若要設定部署伺服器類型，請使用 [**屬性**] 視窗。 設計工具也會產生描述封裝內容的 XML 檔案。 如需詳細資訊，請參閱[建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。

 在部署期間，Internet Information Services （IIS）服務會停止，以將方案檔複製到 SharePoint 伺服器。 藉由使用 Visual Studio 中的封裝設計工具，您可以選取是否應重新開機 Web 服務器。 若要設定解決方案是否部署到前端網頁伺服器或應用程式伺服器，請使用 [**屬性**] 視窗。 如需詳細資訊，請參閱[Solution 元素（solution）](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14))。

### <a name="packaging-explorer"></a>封裝 Explorer
 若要補充功能設計工具和封裝設計工具，您可以使用 [封裝瀏覽器] 將 SharePoint 檔案分組成功能和封裝。 此外，您還可以看到封裝、功能、SharePoint 專案專案和檔案的階層式視圖。 [封裝瀏覽器] 是一個工具視窗，您可以用來完成下列工作：

- 開啟 SharePoint 專案專案和檔案。

- 將 SharePoint 專案專案從一項功能拖放到另一個功能。

- 將 SharePoint 專案專案和功能從一個封裝拖放到另一個套件。

- 將新功能新增至套件。

- 開啟功能或封裝設計工具。

- 驗證功能和封裝。

  Visual Studio 中的 SharePoint 開發工具具有驗證規則，可協助確保解決方案套件的格式正確。 此外，這些規則會確認 *.wsp*方案檔可以成功部署並在 SharePoint 伺服器上啟用。 如需功能之 XML 架構的詳細資訊，請參閱[功能架構](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))。

  您可以將自訂功能和封裝驗證規則加入至 SharePoint 專案系統。 如需詳細資訊，請參閱[如何：建立 SharePoint 方案的自訂功能和封裝驗證規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。

  如需封裝瀏覽器的詳細資訊，請參閱[如何：使用封裝瀏覽器新增和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

### <a name="solution-explorer"></a>方案總管
 您可以使用方案總管來流覽和開啟 SharePoint 專案的檔案。 使用方案總管中的內容功能表來新增功能、功能事件接收器和功能資源。 此外，您可以開啟功能設計工具和封裝設計工具來設定部署的功能和套件。

## <a name="deploy-sharepoint-solutions"></a>部署 SharePoint 方案
 在 Visual Studio 中自訂功能和封裝之後，您可以建立 *.wsp*檔案來部署到 SharePoint 伺服器。 您可以使用 Visual Studio 來進行調試和測試。*wsp*僅適用于開發電腦上的 SharePoint 伺服器。 如需如何將 SharePoint 方案部署至遠端 SharePoint 伺服器的詳細資訊，請參閱[部署方案](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14))。

 您也可以在開發電腦上自訂部署步驟。 如需詳細資訊，請參閱[部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。

## <a name="deploy-files-in-sharepoint-solutions"></a>在 SharePoint 方案中部署檔案
 一般而言，當您將 SharePoint 專案專案加入至 SharePoint 方案時，會包含所有必要的檔案。 可編譯的檔案（程式碼檔案）會內建到方案的輸出元件中。 不過，您可能也必須將無法編譯的檔案（例如 *.xml*、 *.txt*或資源檔）新增至 SharePoint 專案。 這些檔案不會自動封裝在您的方案中。 若要確定它們已封裝，請將檔案加入至對應資料夾或 SharePoint 專案專案。

 當部署方案時，新增至對應資料夾的檔案會自動複製到 SharePoint hive。 新增至 SharePoint 專案專案的檔案會部署到每個檔案的 [**部署位置**] 屬性中指定的位置，而這是根據 [**部署類型**] 屬性部分設定。 根據預設，**部署類型**屬性值為**NoDeployment**，這表示檔案不會與方案一起部署。 您必須為屬性設定另一個值，以將檔案包含在封裝中。

 例如，若要將 *.xml*檔案加入至 SharePoint 專案，請執行下列其中一個動作：

- 將 SharePoint 「版面配置」對應資料夾新增至您的專案。 這會在中建立**方案總管**名為**版面**配置的資料夾，其中包含專案的子資料夾。 將 *.xml*檔案新增至新的子資料夾。 根據預設，檔案會部署至底下的 SharePoint 檔案系統 *。\\\TEMPLATE\LAYOUTS \<Folder Name> *。 如需如何新增對應資料夾的詳細資訊，請參閱[如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

- 將 *.xml*檔案加入至 SharePoint 專案專案的資料夾，然後將 *.xml*檔案的 [**部署類型**] 屬性從**NoDeployment**變更為其他設定，例如**RootFile**或**ElementFile**。 適當的**部署類型**設定取決於檔案和專案。 如需**部署類型**屬性設定的詳細資訊，請參閱[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。

  如果加入的檔案不適用於方案中的任何特定專案，您可以將空的 SharePoint 專案加入方案中，然後在其中新增其他檔案。 將檔案部署至 SharePoint 的另一個替代方案是將模組新增至專案，然後將檔案新增至模組。 如需詳細資訊，請參閱[使用模組來包含方案中的](../sharepoint/using-modules-to-include-files-in-the-solution.md)檔案。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
