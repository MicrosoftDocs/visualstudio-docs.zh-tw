---
title: 發行嚮導（Visual Studio 中的 Office 開發）
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d14abdd9ba6547a3aaf131084168be2e453dd04
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558181"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>發行嚮導（Visual Studio 中的 Office 開發）
  使用 [**發行嚮導]** 將方案檔複製到指定的位置、建立資訊清單檔案，以及建立安裝程式。

 若要存取此 wizard，請在 [**建立**] 功能表上，選擇 [**發佈***解決方案名稱*]。 您也可以從 [**方案總管**] 存取 [**發行嚮導]** 。 開啟專案節點的快捷方式功能表，然後選擇 [**發行**]。

 下一節會說明 wizard 的一頁。

## <a name="where-do-you-want-to-publish-the-application"></a>您要將應用程式發佈到何處？
 **指定要發佈此應用程式的位置**必填。 [發行位置] 是 [**發行嚮導]** 用來複製方案檔的目錄，例如資訊清單、元件、暫存憑證，以及來自組建的其他檔案。 您必須具有這個目錄的寫入權限。

 將 [位置] 輸入為 [磁片路徑]、[檔案共用]、[FTP 網站] 或 [網站 URL]，或按一下 [**流覽]** 按鈕以流覽位置。 路徑可以是下列格式：

- 標準 Windows 格式的相對或絕對路徑，例如*C:\Deploy\MyApplication*或 *\MyApplication*。

- 通用命名慣例（UNC）路徑，例如 *\\\ServerName\MyApplication\\* 。

- 網站的 URL，例如 `http://www.contoso.com/MyApplication`。

  根據預設，如果您已安裝 IIS，則發佈位置會 *http://localhost/projectname/* ，如果您未安裝 iis，則為 publish \ 目錄。

> [!NOTE]
> 如果目的電腦執行的是 Windows Vista，還有其他考慮。 您必須是 Windows Vista 電腦上的系統管理員，才能使用 [本機發佈] 選項。 此外，不論您是否已安裝 IIS，預設位置一律會是 [*發行\\* 目錄]。

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>終端使用者電腦上的預設安裝路徑為何？
 安裝路徑是選擇性的。 如果您想要的話，可以稍後再設定安裝路徑。 如需詳細資訊，請參閱[如何：變更 Office 方案的安裝路徑](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。

 安裝路徑是終端使用者將從中安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 [**發行] 嚮導**不會將解決方案部署到這個位置，除非該路徑與您在上一頁的 [**指定要發行此應用程式的位置**] 方塊中輸入的路徑相同。

 **從網站**指定終端使用者安裝解決方案所遵循的 URL。

 **從 UNC 路徑或檔案共用**指定終端使用者安裝解決方案時將遵循的 UNC 路徑。

 **從 cd-rom 或 dvd-rom**此選項不需要安裝路徑。

 Visual Studio 不會燒錄 CD 或 DVD。 您必須手動將輸出複製到 CD 或 DVD。

## <a name="see-also"></a>另請參閱
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Visual Studio 中的 [發行&#40;] 頁面、[專案設計工具] Office 開發&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
