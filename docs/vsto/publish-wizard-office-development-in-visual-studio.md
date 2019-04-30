---
title: 發行精靈 （在 Visual Studio 中的 Office 程式開發）
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
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447065"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>發行精靈 （在 Visual Studio 中的 Office 程式開發）
  使用**發行精靈**將方案檔複製到指定的位置，建立資訊清單的檔案，並建立安裝程式。

 若要存取此精靈時，在**建置**功能表上，選擇**發佈** *SolutionName*。 您也可以存取**發行精靈**從**方案總管 中**。 開啟 [專案] 節點的捷徑功能表，然後選擇**發佈**。

 每一節說明精靈的頁面。

## <a name="where-do-you-want-to-publish-the-application"></a>您要在其中發行應用程式？
 **指定要發行此應用程式的位置**所需。 發行位置為目錄，其中**發行精靈**從組建複製資訊清單、 組件、 暫時憑證和其他檔案等方案檔。 您必須具有這個目錄的寫入權限。

 輸入該位置的磁碟路徑、 檔案共用、 FTP 站台或網站 URL，或按一下**瀏覽**以瀏覽位置 按鈕。 路徑可以是下列格式：

- 相對或絕對路徑在標準 Windows 格式，例如*C:\Deploy\MyApplication*或是*\MyApplication*。

- 通用命名慣例 (UNC) 路徑，例如 *\\\ServerName\MyApplication\\*。

- URL 的 web 站台，例如 http://www.microsoft.com/MyApplication。

  根據預設，發佈的位置是否*http://localhost/projectname/* 有 IIS 安裝，或如果您這樣做，則為 publish\ 目錄未安裝 IIS。

> [!NOTE]
> 如果目標電腦執行 Windows Vista，則需要有更多的考量。 您必須是 Windows Vista 電腦上的系統管理員，才能使用本機發行選項。 另外，預設位置是永遠*發佈\\*目錄下，不論您是否已安裝 IIS。

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>使用者電腦上的預設安裝路徑為何？
 安裝路徑是選擇性的。 如果您想，您可以稍後再設定安裝路徑。 如需詳細資訊，請參閱[如何：變更 Office 方案的安裝路徑](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。

 安裝路徑是在終端使用者會安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 **發行精靈**不會部署方案到這個位置，除非此路徑中輸入一個相同**指定要發行此應用程式的位置**前一頁上的方塊。

 **從網站**指定使用者在安裝方案的 URL。

 **從 UNC 路徑或檔案共用**指定 UNC 路徑的使用者將遵循安裝方案。

 **從 CD-ROM 或 DVD-ROM**這個選項就不需要安裝路徑。

 Visual Studio 不會不會燒錄 CD 或 DVD。 您必須手動將輸出複製到 CD 或 DVD。

## <a name="see-also"></a>另請參閱
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [發行頁面、 專案設計工具&#40;在 Visual Studio 中的 Office 程式開發&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
