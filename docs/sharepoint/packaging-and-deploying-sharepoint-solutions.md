---
title: "封裝和部署 SharePoint 方案 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e25d0829305f414712590296b6121d62583736a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>封裝和部署 SharePoint 方案
  一般而言，SharePoint 方案部署到 SharePoint 伺服器使用方案套件 (.wsp) 檔案。 您可以使用 Visual Studio，將您的 SharePoint 專案項目組織成功能，以及建立套件以部署您的 SharePoint 功能。  
  
 本主題提供下列資訊：  
  
-   [建立功能和封裝](#Creating)  
  
-   [功能和封裝工具支援](#Tools)  
  
-   [部署 SharePoint 方案](#Deploying)  
  
-   [部署 SharePoint 方案中的檔案](#DeployingFiles)  
  
##  <a name="Creating"></a>建立功能和封裝  
 您可以使用 Visual Studio 來分組到相關的 SharePoint 項目*功能*。 例如，連絡人清單定義的功能可能包含清單執行個體和清單定義。 您可以將這兩個元素合併成單一功能進行部署。 如需有關功能的詳細資訊，請參閱[建置組塊： 功能](http://go.microsoft.com/fwlink/?LinkID=169183)。  
  
 接下來，您可以建立 SharePoint 方案套件 (.wsp) 包裝成單一套件的多個功能、 網站定義、 組件和其他檔案的檔案儲存在 SharePoint 部署至伺服器的檔案所需的格式。 如需詳細資訊，請參閱[建置組塊： 方案](http://go.microsoft.com/fwlink/?LinkID=169186)。  
  
##  <a name="Tools"></a>功能和封裝工具支援  
 您可以使用 Visual Studio 中的 SharePoint 開發工具，快速地將 SharePoint 檔案組織成功能 」 和更容易進行部署的方案套件。 您可以使用下列工具來設定功能和方案套件。  
  
-   功能設計工具和封裝設計工具。  
  
-   封裝總管 中，工具視窗。  
  
-   方案總管 中。  
  
### <a name="feature-designer-and-package-designer"></a>功能設計工具和封裝設計工具  
 您可以建立功能、 設定範圍，並標示為相依性的其他功能，使用功能設計工具。 在設計工具也會顯示最後的 XML 檔案描述每項功能。 如需詳細資訊，請參閱[建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。  
  
 套用至特定網站或網站的群組的功能，藉由設定其*範圍*功能設計工具中。 如果對個別網站啟動功能，則表示功能僅適用於該特定網站中。 如果針對網站集合啟用功能，功能中的項目會套用至整個網站集合。 如需詳細資訊，請參閱[項目範圍內](http://go.microsoft.com/fwlink/?LinkID=169189)。  
  
 如果您的功能會依賴其他功能，您可以設定*功能啟用相依性*標記之前提供您的功能相依的功能。 功能啟用相依性檢查相依的功能都已經在該範圍中啟動。 如需詳細資訊，請參閱[啟用相依性和範圍](http://go.microsoft.com/fwlink/?LinkID=169190)。  
  
 在封裝設計工具中，您可以 SharePoint 項目群組成單一方案套件，並設定是否要在部署期間重設 Web 伺服器。 若要設定部署伺服器類型，請使用**屬性**視窗。 在設計工具也會產生描述套件內容的 XML 檔案。 如需詳細資訊，請參閱[建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。  
  
 在部署期間，網際網路資訊服務 (IIS) 服務已停止，將方案檔複製到 SharePoint 伺服器。 在 Visual Studio 中使用封裝設計工具，您可以選取是否應該重新啟動 Web 伺服器。 若要設定前端網頁伺服器或應用程式伺服器部署方案時，使用**屬性**視窗。 如需詳細資訊，請參閱[方案項目 （方案）](http://go.microsoft.com/fwlink/?LinkID=169191)。  
  
### <a name="packaging-explorer"></a>封裝總管  
 若要補充的功能設計工具和封裝設計工具，您可以使用 [封裝總管] 來分組功能和封裝中的 SharePoint 檔案。 此外，請參閱階層式檢視的封裝時，功能，SharePoint 專案項目和檔案。 [封裝總管] 是工具視窗可讓您完成下列工作：  
  
-   開啟 SharePoint 專案項目和檔案。  
  
-   拖放的其中一項功能的 SharePoint 專案項目到另一個。  
  
-   拖放 SharePoint 專案項目和功能從某個封裝到另一個。  
  
-   將新功能加入封裝。  
  
-   開啟功能或封裝的設計工具。  
  
-   驗證功能和封裝。  
  
 在 Visual Studio 中的 SharePoint 開發工具有驗證規則，以協助確保方案套件正確。 此外，規則驗證的.wsp 方案檔可以成功部署或在 SharePoint 伺服器上啟動。 如需有關 XML 結構描述的功能，請參閱[功能結構描述](http://go.microsoft.com/fwlink/?LinkID=169192)。  
  
 您可以將自訂功能和封裝驗證規則加入至 SharePoint 專案系統。 如需詳細資訊，請參閱[How to： 建立自訂功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。  
  
 如需 [封裝總管] 的詳細資訊，請參閱[如何： 新增與移除功能和封裝的項目使用封裝總管](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
### <a name="solution-explorer"></a>底下提供說明，包括方案總管  
 您可以使用 [方案總管] 中瀏覽並開啟 SharePoint 專案的檔案。 在 [方案總管] 中使用操作功能表，新增功能，功能事件接收器，和功能的資源。 此外，您可以開啟功能設計工具與封裝設計工具，若要設定的功能和部署的套件。  
  
##  <a name="Deploying"></a>部署 SharePoint 方案  
 自訂功能和 Visual Studio 中的封裝之後，您可以建立要部署到 SharePoint 伺服器的.wsp 檔案。 您可以使用 Visual Studio 偵錯及測試，在開發電腦上的 SharePoint 伺服器上才.wsp。 如需如何將 SharePoint 方案部署至遠端 SharePoint 伺服器的詳細資訊，請參閱[部署解決方案](http://go.microsoft.com/fwlink/?LinkID=169194)。  
  
 您也可以自訂部署步驟，在開發電腦上。 如需詳細資訊，請參閱[部署、 發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
##  <a name="DeployingFiles"></a>部署 SharePoint 方案中的檔案  
 一般而言，當您將 SharePoint 專案項目加入 SharePoint 方案時，所有必要的檔案會包含。 檔案可能是編譯 （程式碼檔案） 全都會建置到輸出組件的方案。 不過，您也可能要將非可編譯的檔案，例如，.xml、.txt 或資源檔加入至 SharePoint 專案。 這些檔案不會自動封裝在您的方案中。 若要確保封裝，請新增檔案至對應的資料夾或 SharePoint 專案項目。  
  
 部署方案時，會自動加入至對應的資料夾檔案複製到 SharePoint 登錄區。 部署檔案加入至 SharePoint 專案項目中指定的位置到**部署位置**每個檔案，部分設定的屬性根據**部署類型**屬性。 根據預設，**部署類型**屬性值是**NoDeployment**，這表示不會隨著方案部署的檔案。 您必須設定為包含在封裝中的檔案屬性的另一個值。  
  
 例如，如果要將.xml 檔案加入至 SharePoint 專案，請執行其中一個動作：  
  
-   專案中加入 SharePoint"配置 」 對應資料夾。 這會建立在**方案總管 中**資料夾，名為**配置**具有專案子資料夾。 加入新的子資料夾中的.xml 檔案。 根據預設，SharePoint 檔案系統 來部署檔案...\TEMPLATE\LAYOUTS\\*資料夾名稱*\\。 如需如何新增對應的資料夾資訊，請參閱[如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
-   加入至 SharePoint 專案項目資料夾的.xml 檔案，然後變更**部署類型**屬性的.xml 檔案**NoDeployment**給另一個設定，例如**RootFile**或**ElementFile**。 適當**部署類型**設定取決於檔案和專案。 如需有關**部署類型**屬性設定，請參閱[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。  
  
 如果加入的檔案不會套用至任何特定專案方案中，您可以將空白的 SharePoint 專案加入方案中，並將其他檔案新增到它。 特別至內容資料庫中，將檔案部署至 SharePoint，另一個替代方式是將模組加入至專案，然後將檔案新增至模組。 如需詳細資訊，請參閱[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## <a name="see-also"></a>請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  