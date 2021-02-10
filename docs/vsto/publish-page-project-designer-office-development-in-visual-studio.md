---
title: 'Office 開發 (發佈頁面、專案設計工具) '
description: 瞭解 Visual Studio 中的 [專案設計工具] 的 [發行] 頁面，如何用來設定部署的屬性。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc80a71516f1de8f2a6943d9df7b02341ea786aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971722"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Visual Studio) 中的 [發行] 頁面、[專案設計工具] (Office 開發
  [專案設計工具]  的 [發行]  頁面，可用以設定部署的屬性。

 若要存取此頁面，請在 **方案總管** 中選取專案，然後在 [**專案**] 功能表上，選擇 [專案 *名稱***屬性**]。 如果未顯示 [發行]  頁面，請選擇 [發行]  索引標籤。

> [!NOTE]
> 您也可以在 [發行精靈] 中設定發行位置。 如需詳細資訊，請參閱 [如何：使用 ClickOnce 發行 Office 方案](/previous-versions/bb386095(v=vs.110))。

## <a name="uielement-list"></a>UIElement 清單
 **發佈資料夾位置 (網站、ftp 伺服器或檔案路徑)** 必填。

 發行資料夾位置是 Visual Studio 從組建複製資訊清單、組件及其他檔案等方案檔的目的地目錄。 您必須具有這個目錄的寫入權限。

 選項包括本機電腦、UNC 檔案共用或 HTTP/HTTPS 網站。 路徑可以是本機 (*c:\foldername\publishfolder*) 、相對 (*發行 \\*) 或完整位置 (*\\ \servername\foldername* 或 HTTP://<em>servername/資料夾名稱</em>) 。

 依預設， *http://localhost/projectname/* 如果您已安裝 iis，發行位置為，如果您沒有安裝 iis， *\\ 則發佈* 目錄。

 **安裝資料夾 URL** 選。

 安裝資料夾 URL 是使用者將從中安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 路徑可以與發行資料夾位置相同，但這並非必要條件。

 選項包括本機電腦、UNC 檔案共用或 HTTP/HTTPS 網站。 路徑可以是本機 (*c:\foldername\publishfolder*) 、相對 (*發行 \\*) 或完整位置 (*\\ \servername\foldername* 或 HTTP://<em>servername/資料夾名稱</em>) 。 所有的 HTTP/HTTPS 位置都必須以 US-ASCII 字元建立。 不支援 Unicode 字元。

 如果已設定安裝路徑，自訂檔案必須位於該位置，使用者才能安裝自訂。 只有在知道最終部署位置時，才應該設定位置。

 如果安裝檔案位於相對於文件或安裝程式的位置，例如使用 CD 選項，請將這個方塊保留空白。

 系統管理員稍後可以指派這個值。 如需詳細資訊，請參閱 [如何：變更 Office 方案的安裝路徑](/previous-versions/bb608626(v=vs.110))。

 **必要條件** 必要條件可以包含在安裝程式中，或在安裝期間依需求下載。

- **從元件廠商的網站下載必要條件**：使用這個選項可從 Microsoft 下載這些必要條件。

- **從應用程式的相同位置下載必要條件**：使用這個選項可將必要條件封裝在安裝程式中。 將必要條件檔案包含在安裝程式中會增加方案的大小。

- **從下列位置下載必要條件**：使用這個選項可透過網頁或網路共用上的另一個安裝程式，將必要條件另外提供給使用者。

  **更新** 更新間隔會決定方案檢查更新的頻率。 預設值為每七天檢查一次。

  每次載入文件層級自訂或 VSTO 增益集時便檢查更新，雖然可以保持在最新狀態，但也會影響啟動效能。

  如果您要使用 CD 或卸除式磁碟機進行部署，請將這個選項設定為 [永遠不檢查更新] 。

  **選項 (描述)** 您可以設定下列屬性的發佈選項：

- 發行語言：Office 方案的地區設定。

- 發行者名稱：出現在 [新增/移除程式]  或 [程式和功能] 中的公司或開發人員名稱。

- 產品名稱：出現在 [新增/移除程式]  或 [程式和功能] 中的 Office 方案名稱。

- 支援 URL：使用者連絡 Office 方案技術支援的位置。

  **(Office 設定的選項)** 您可以設定下列屬性的發佈選項：

- 方案名稱：出現在 Office 應用程式中的 Office 方案名稱。

- 描述：出現在 Office 應用程式中的 Office 方案描述。

- VSTO 增益集載入行為。

  - 啟動時載入：指定在 Office 應用程式啟動時載入 VSTO 增益集。

  - 視需要載入：指定只有在應用程式需要時才載入 VSTO 增益集，例如當使用者按一下使用 VSTO 增益集功能的 UI 項目時。

  **發行語言** 此選項會設定 Microsoft 軟體授權條款的語言，並在必要條件清單中包含語言套件。 它不會影響自訂的語言。 安裝程式中的語言取決於 Visual Studio 已安裝的語言。

  如需如何變更 **發行語言** 的詳細資訊，請參閱 [如何：變更 ClickOnce 應用程式的發行語言](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)。

  **發佈版本** 設定自訂的版本號碼。 當版本號碼變更時，應用程式會以更新的形式發行。 在建置程序期間，會針對每個版本建立新的資料夾，以避免覆寫先前發行的版本。 發行版本的每個部分 (**主要**、 **次要**、 **組建**、 **修訂**) 最多可包含 5 個數字。

  **每次發行時自動遞增修訂** 選。 選取時 (預設)，每次發行一次自訂，版本號碼的 **修訂** 部分都會加一。 這會使得自訂以更新的形式發行。

  **立即發佈** 使用目前的設定發佈應用程式。 這相當於 [發行精靈]  中的 [完成] 按鈕。

## <a name="see-also"></a>另請參閱

- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [部署的 Office 解決方案必要條件](/previous-versions/bb608617(v=vs.110))