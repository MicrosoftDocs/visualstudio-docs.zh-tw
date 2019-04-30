---
title: 發行 Page，Project Designer （Visual Studio 中的 Office 程式開發）
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84a62fc796243172c9130c8113c4e6d289ed3092
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447010"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>發行 Page，Project Designer （Visual Studio 中的 Office 程式開發）
  [專案設計工具]  的 [發行]  頁面，可用以設定部署的屬性。

 若要存取此頁面，選取 [] 中的專案**方案總管**，然後在**專案**功能表上，選擇*Projectname* **屬性**. 如果未顯示 [發行]  頁面，請選擇 [發行]  索引標籤。

> [!NOTE]
> 您也可以在 [發行精靈] 中設定發行位置。 如需詳細資訊，請參閱[如何：使用 ClickOnce 發行 Office 方案](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)。

## <a name="uielement-list"></a>UIElement 清單
 **發行資料夾位置 （網站、 ftp 伺服器或檔案路徑）** 所需。

 發行資料夾位置是 Visual Studio 從組建複製資訊清單、組件及其他檔案等方案檔的目的地目錄。 您必須具有這個目錄的寫入權限。

 選項包括本機電腦、UNC 檔案共用或 HTTP/HTTPS 網站。 路徑可以是本機 (*c:\foldername\publishfolder*)，相對於 (*發佈\\*)，或完整限定的位置 (*\\\servername\foldername*或 http://<em>servername/foldername</em>)。

 根據預設，發行位置是*http://localhost/projectname/* 如果您有安裝了 IIS，則*發行\\*目錄，如果您不需要安裝 IIS。

 **安裝資料夾 URL**選擇性。

 安裝資料夾 URL 是使用者將從中安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 路徑可以與發行資料夾位置相同，但這並非必要條件。

 選項包括本機電腦、UNC 檔案共用或 HTTP/HTTPS 網站。 路徑可以是本機 (*c:\foldername\publishfolder*)，相對於 (*發佈\\*)，或完整限定的位置 (*\\\servername\foldername*或 http://<em>servername/foldername</em>)。 所有的 HTTP/HTTPS 位置都必須以 US-ASCII 字元建立。 不支援 Unicode 字元。

 如果已設定安裝路徑，自訂檔案必須位於該位置，使用者才能安裝自訂。 只有在知道最終部署位置時，才應該設定位置。

 如果安裝檔案位於相對於文件或安裝程式的位置，例如使用 CD 選項，請將這個方塊保留空白。

 系統管理員稍後可以指派這個值。 如需詳細資訊，請參閱[如何：變更 Office 方案的安裝路徑](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。

 **必要條件**必要條件可以包含與安裝程式，或視需要在安裝期間下載。

- **從元件廠商的網站下載必要條件**:使用此選項可從 Microsoft 下載這些必要條件。

- **從與我的應用程式相同的位置下載必要條件**:若要將必要條件封裝在安裝程式中使用此選項。 將必要條件檔案包含在安裝程式中會增加方案的大小。

- **從下列位置下載必要條件**:使用此選項可將必要條件提供給終端使用者個別網頁或網路共用上的另一個安裝程式。

  **更新**更新間隔決定方案檢查更新的頻率。 預設值為每七天檢查一次。

  每次載入文件層級自訂或 VSTO 增益集時便檢查更新，雖然可以保持在最新狀態，但也會影響啟動效能。

  如果您要使用 CD 或卸除式磁碟機進行部署，請將這個選項設定為 [永遠不檢查更新] 。

  **選項 （描述）** 可以設定下列屬性的發行選項：

- 發行語言：Office 方案的地區設定。

- 發行者名稱：出現在 [新增/移除程式]  或 [程式和功能] 中的公司或開發人員名稱。

- 產品名稱：出現在 [新增/移除程式]  或 [程式和功能] 中的 Office 方案名稱。

- 支援 URL：使用者連絡 Office 方案技術支援的位置。

  **選項 （Office 設定）** 可以設定下列屬性的發行選項：

- 方案名稱：出現在 Office 應用程式中的 Office 方案名稱。

- 描述：出現在 Office 應用程式中的 Office 方案描述。

- VSTO 增益集載入行為。

  - 啟動時載入：指定在 Office 應用程式啟動時載入 VSTO 增益集。

  - 視需要載入：指定只有在應用程式需要時才載入 VSTO 增益集，例如當使用者按一下使用 VSTO 增益集功能的 UI 項目時。

  **發行語言**這個選項設定的語言的 Microsoft 軟體授權條款，並將語言套件包含在必要條件清單中。 它不會影響自訂的語言。 安裝程式中的語言取決於 Visual Studio 已安裝的語言。

  如需有關如何變更**發行語言**，請參閱[How to:變更 ClickOnce 應用程式的發行語言](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)。

  **發行版本**設定自訂的版本號碼。 當版本號碼變更時，應用程式會以更新的形式發行。 在建置程序期間，會針對每個版本建立新的資料夾，以避免覆寫先前發行的版本。 發行版本的每個部分 (**主要**、 **次要**、 **組建**、 **修訂**) 最多可包含 5 個數字。

  **隨著每次發行自動遞增修訂**選擇性。 選取時 (預設)，每次發行一次自訂，版本號碼的 **修訂** 部分都會加一。 這會使得自訂以更新的形式發行。

  **立即發行**發行所使用的目前設定的應用程式。 這相當於 [發行精靈]  中的 [完成] 按鈕。

## <a name="see-also"></a>另請參閱

- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office 方案的部署必要條件](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
