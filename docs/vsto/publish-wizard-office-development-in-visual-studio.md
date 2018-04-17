---
title: 發行精靈 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67e3222c6f1deeca58b84aca4ba73d2826483b26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>發行精靈 (Visual Studio 中的 Office 程式開發)
  使用**發行精靈**將方案檔複製到指定的位置，建立資訊清單檔案，並建立安裝程式。  
  
 若要存取此精靈時，在**建置**功能表上，選擇**發行** *SolutionName*。 您也可以存取**發行精靈**從**方案總管 中**。 開啟 [專案] 節點的捷徑功能表，然後選擇**發行**。  
  
 下列每個章節描述精靈頁面。  
  
## <a name="where-do-you-want-to-publish-the-application"></a>您要在其中發行應用程式？  
 **指定要發行此應用程式的位置**  
 必要。 發行位置是目錄位置**發行精靈**從組建複製資訊清單、 組件、 暫時憑證和其他檔案等方案檔。 您必須具有這個目錄的寫入權限。  
  
 輸入該位置的磁碟路徑、 檔案共用、 FTP 站台或網站的 URL，或按一下**瀏覽**按鈕來瀏覽的位置。 路徑可以是下列格式：  
  
-   標準 Windows 格式，例如 C:\Deploy\MyApplication 或 \MyApplication 的相對或絕對路徑。  
  
-   通用命名慣例 (UNC) 路徑，例如\\\ServerName\MyApplication\\。  
  
-   URL 的 web 站台，例如http://www.microsoft.com/MyApplication。  
  
 根據預設，發行位置是*http://localhost/projectname/*是否已安裝了 IIS，則為 publish\ 目錄如果您未安裝 IIS。  
  
> [!NOTE]  
>  如果目標電腦執行 Windows Vista，則需要有多個考量。 您必須是 Windows Vista 電腦上的系統管理員，才能使用本機發行選項。 此外的預設位置是一律*發行\\*目錄下，不論您是否已安裝 IIS。  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>終端使用者電腦上的預設安裝路徑為何？  
 安裝路徑是選擇性的。 稍後如果您想要的話，您可以設定安裝路徑。 如需詳細資訊，請參閱[如何： 變更 Office 方案的安裝路徑](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。  
  
 安裝路徑是終端使用者將從中安裝自訂的目錄。 它也是方案將會用來檢查更新的路徑。 **發行精靈**並未部署方案到這個位置，除非此路徑中輸入相同**指定要發行此應用程式位置**前一頁上的方塊。  
  
 **從網站**  
 指定使用者在安裝方案的 URL。  
  
 **從 UNC 路徑或檔案共用**  
 指定使用者在安裝方案的 UNC 路徑。  
  
 **從 CD-ROM 或 DVD-ROM**  
 這個選項就不需要安裝路徑。  
  
 Visual Studio 不會不燒錄 CD 或 DVD。 您必須手動將輸出複製到 CD 或 DVD。  
  
## <a name="see-also"></a>另請參閱  
 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [專案設計工具、 發行頁&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  