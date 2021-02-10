---
title: 在 Visual Studio) 中發佈嚮導 (Office 開發
description: 瞭解如何使用 [發佈嚮導] 將方案檔複製到指定的位置、建立資訊清單檔案，以及在 Visual Studio 中建立安裝程式。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29400e82dcd7b0d5cd9062679610b50bfaab191d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971683"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>在 Visual Studio) 中發佈嚮導 (Office 開發
  使用 [ **發佈嚮導]** 將方案檔複製到指定的位置、建立資訊清單檔案，以及建立安裝程式。

 若要存取此嚮導，請在 [**組建**] 功能表上，選擇 [**發行***解決方案名稱*]。 您也可以從 **方案總管** 存取 [**發佈嚮導]** 。 開啟專案節點的快捷方式功能表，然後選擇 [ **發行**]。

 以下各節說明嚮導的頁面。

## <a name="where-do-you-want-to-publish-the-application"></a>您要將應用程式發佈至何處？
 **指定要發佈此應用程式的位置** 必填。 發佈位置是 **發佈嚮導** 從中複製方案檔的目錄，例如資訊清單、元件、暫時憑證，以及來自組建的其他檔案。 您必須具有這個目錄的寫入權限。

 將 [位置] 輸入為磁片路徑、檔案共用、FTP 網站或網站 URL，或按一下 [ **流覽]** 按鈕來流覽位置。 路徑可以是下列格式：

- 標準 Windows 格式的相對或絕對路徑，例如 *C:\Deploy\MyApplication* 或 *\MyApplication*。

- 通用命名慣例 (UNC) 路徑，例如 *\\ \ServerName\MyApplication \\*。

- 網站的 URL，例如 `http://www.contoso.com/MyApplication` 。

  依預設，如果您已 *http://localhost/projectname/* 安裝 iis，發行位置為，如果您沒有安裝 iis，則發佈目錄。

> [!NOTE]
> 如果目的電腦執行的是 Windows Vista，還有其他考慮。 您必須是 Windows Vista 電腦上的系統管理員，才能使用本機發佈選項。 此外，不論您是否已安裝 IIS，預設的位置一律會是 *發佈 \\* 目錄。

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>終端使用者電腦上的預設安裝路徑為何？
 安裝路徑是選擇性的。 如果您想要的話，您可以稍後再設定安裝路徑。 如需詳細資訊，請參閱 [如何：變更 Office 方案的安裝路徑](/previous-versions/bb608626(v=vs.110))。

 安裝路徑是使用者將安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 除非路徑與您在上一個頁面的 [**指定要發佈此應用程式的位置**] 方塊中輸入的路徑相同，否則 **發佈嚮導** 不會將解決方案部署到這個位置。

 **從網站** 指定使用者將遵循以安裝方案的 URL。

 **從 UNC 路徑或檔案共用** 指定使用者將遵循以安裝解決方案的 UNC 路徑。

 **從 cd-rom 或 dvd-rom** 此選項不需要安裝路徑。

 Visual Studio 不會燒錄 CD 或 DVD。 您必須手動將輸出複製到 CD 或 DVD。

## <a name="see-also"></a>另請參閱
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Visual Studio&#41;中的 [發行] 頁面、[專案設計工具] &#40;Office 開發 ](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)