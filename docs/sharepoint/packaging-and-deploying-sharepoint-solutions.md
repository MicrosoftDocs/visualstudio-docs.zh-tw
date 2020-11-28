---
title: 封裝和部署 SharePoint 方案 |Microsoft Docs
description: 封裝和部署 SharePoint 方案，這些方案是使用方案套件 ( .wsp) 檔案部署到 SharePoint 伺服器。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bd06a5be3c9e7ceea38bdb4560f8b6262175bd45
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305072"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>封裝和部署 SharePoint 方案
  SharePoint 方案通常會使用 ( .wsp) 檔案的方案套件，部署到 SharePoint 伺服器。 您可以使用 Visual Studio 將 SharePoint 專案專案組織成功能，並建立封裝以部署 SharePoint 功能。

 此主題提供下列資訊：

- [建立功能和套件](#create-features-and-packages)

- [功能與封裝工具支援](#feature-and-packaging-tool-support)

- [部署 SharePoint 方案](#deploy-sharepoint-solutions)

- [在 SharePoint 方案中部署檔案](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>建立功能和套件
 您可以使用 Visual Studio 將相關的 SharePoint 元素群組為 *功能*。 例如，連絡人清單定義的功能可能包括清單實例和清單定義。 您可以將這兩個元素合併成單一功能，以供部署之用。 如需功能的詳細資訊，請參閱 [建立區塊：功能](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))。

 接下來，您可以建立 SharePoint 方案套件， (*.wsp*) 將多個功能、網站定義、元件及其他檔案組合成單一套件，以 SharePoint 所需的格式儲存檔案，以將檔案部署至伺服器。 如需詳細資訊，請參閱 [建立區塊：方案](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14))。

## <a name="feature-and-packaging-tool-support"></a>功能與封裝工具支援
 您可以使用 Visual Studio 中的 SharePoint 開發工具，快速地將 SharePoint 檔案組織成功能和方案套件，以方便部署。 您可以使用下列工具來設定功能和方案套件。

- 功能設計工具和封裝設計工具。

- 封裝 Explorer，也就是工具視窗。

- 方案總管。

### <a name="feature-designer-and-package-designer"></a>功能設計工具和封裝設計工具
 您可以使用 [功能設計工具] 來建立功能、設定範圍，以及將其他功能標示為相依性。 設計工具也會顯示描述每項功能的最終 XML 檔案。 如需詳細資訊，請參閱 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。

 將功能套用至特定網站或網站群組，方法是在功能設計工具中設定其 *範圍* 。 如果已針對個別網站啟用某項功能，此功能僅適用于該特定網站。 如果已針對網站集合啟用功能，則功能中的專案會套用至整個網站集合。 如需詳細資訊，請參閱 [元素範圍](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14))。

 如果您的功能依賴其他功能，您可以設定 *功能啟用* 相依性來標記相依功能，然後再讓您的功能可供使用。 功能啟用相依性會檢查是否已在該範圍啟用相依功能。 如需詳細資訊，請參閱啟用相依性 [和範圍](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14))。

 在封裝設計工具中，您可以將 SharePoint 元素群組成單一方案套件，並設定是否要在部署期間重設 Web 服務器。 若要設定部署伺服器類型，請使用 [ **屬性** ] 視窗。 設計工具也會產生描述套件內容的 XML 檔。 如需詳細資訊，請參閱 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。

 在部署期間，Internet Information Services (IIS) 服務會停止，以將方案檔複製到 SharePoint 伺服器。 您可以使用 Visual Studio 中的封裝設計工具，選擇是否要重新開機 Web 服務器。 若要設定解決方案是部署到前端網頁伺服器或應用程式伺服器，請使用 [ **屬性** ] 視窗。 如需詳細資訊，請參閱 solution [Element (solution) ](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14))。

### <a name="packaging-explorer"></a>封裝 Explorer
 若要補充功能設計工具和封裝設計工具，您可以使用封裝瀏覽器將 SharePoint 檔案群組成功能和套件。 此外，您可以看到套件、功能、SharePoint 專案專案和檔案的階層式視圖。 封裝瀏覽器是一種工具視窗，您可以用來完成下列工作：

- 開啟 SharePoint 專案專案和檔案。

- 將 SharePoint 專案專案從某個功能拖放到另一個功能。

- 將 SharePoint 專案專案和功能從一個封裝拖放到另一個套件。

- 將新功能新增至套件。

- 開啟功能或封裝設計工具。

- 驗證功能和套件。

  Visual Studio 中的 SharePoint 開發工具具有驗證規則，可協助確保方案套件的格式正確。 此外，這些規則會確認 *.wsp* 方案檔是否可以在 SharePoint 伺服器上順利部署和啟用。 如需功能之 XML 架構的詳細資訊，請參閱 [功能架構](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))。

  您可以將自訂功能和封裝驗證規則加入至 SharePoint 專案系統。 如需詳細資訊，請參閱 [如何：建立 SharePoint 方案的自訂功能和封裝驗證規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。

  如需封裝瀏覽器的詳細資訊，請參閱 [如何：使用封裝瀏覽器加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。

### <a name="solution-explorer"></a>方案總管
 您可以使用方案總管來流覽和開啟 SharePoint 專案的檔案。 使用方案總管中的內容功能表來新增功能、功能事件接收器和功能資源。 此外，您可以開啟 [功能設計工具] 和 [封裝設計工具] 來設定部署的功能和套件。

## <a name="deploy-sharepoint-solutions"></a>部署 SharePoint 方案
 在 Visual Studio 中自訂功能和封裝之後，您可以建立要部署到 SharePoint 伺服器的 *.wsp* 檔。 您可以使用 Visual Studio 來進行 debug 和 test。在開發電腦上的 SharePoint 伺服器上僅限 *wsp* 。 如需如何將 SharePoint 方案部署到遠端 SharePoint 伺服器的詳細資訊，請參閱 [部署方案](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14))。

 您也可以在開發電腦上自訂部署步驟。 如需詳細資訊，請參閱 [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。

## <a name="deploy-files-in-sharepoint-solutions"></a>在 SharePoint 方案中部署檔案
 一般來說，當您將 SharePoint 專案專案加入至 SharePoint 方案時，會包含所有必要的檔案。 可 (程式碼檔編譯) 內建于方案的輸出元件中的檔案。 不過，您可能也必須將無法編譯的檔案（例如 *.xml*、 *.txt* 或資源檔）加入至 SharePoint 專案。 這些檔案不會自動封裝在您的解決方案中。 若要確定封裝已封裝，請將檔案加入至對應的資料夾或 SharePoint 專案專案中。

 部署方案時，新增至對應資料夾的檔案會自動複製到 SharePoint hive。 新增至 SharePoint 專案專案的檔案會部署到每個檔案的 [ **部署位置** ] 屬性中所指定的位置，此位置是根據 [ **部署類型** ] 屬性部分設定的。 **部署類型** 屬性值預設為 **NoDeployment**，這表示該檔案不會與方案一起部署。 您必須設定屬性的另一個值，以將檔案包含在封裝中。

 例如，若要將 *.xml* 檔案加入至 SharePoint 專案，請執行下列其中一項動作：

- 將 SharePoint 「版面配置」對應資料夾新增至您的專案。 這會在 **方案總管** 名為 **版面** 配置的資料夾中建立專案的子資料夾。 將 *.xml* 檔案新增至新的子資料夾。 根據預設，檔案會部署到下的 SharePoint 檔 *系統。\\\TEMPLATE\LAYOUTS \<Folder Name>*。 如需如何加入對應資料夾的詳細資訊，請參閱 [如何：加入和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

- 將 *.xml* 檔案新增至 SharePoint 專案專案的資料夾，然後將 *.xml* 檔案的 [**部署類型**] 屬性從 **NoDeployment** 變更為其他設定，例如 **RootFile** 或 **ElementFile**。 適當的 **部署類型** 設定取決於檔案和專案。 如需 **部署類型** 屬性設定的詳細資訊，請參閱 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。

  如果新增的檔案未套用至方案中的任何特定專案，您可以將空白的 SharePoint 專案加入至方案，然後在其中加入其他檔案。 另一個將檔案部署至 SharePoint 的替代方案（特別是針對內容資料庫）是將模組加入至專案，然後將檔案新增至模組。 如需詳細資訊，請參閱 [使用模組來包含方案中的](../sharepoint/using-modules-to-include-files-in-the-solution.md)檔案。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
