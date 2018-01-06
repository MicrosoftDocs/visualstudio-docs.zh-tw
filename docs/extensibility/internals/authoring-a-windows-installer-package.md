---
title: "撰寫的 Windows Installer 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2055f57e78c348f3f8e53187126588f382f0b944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-a-windows-installer-package"></a>撰寫的 Windows Installer 封裝
資料磁碟機的 Windows Installer 模型。 不用撰寫程序的指令碼，將檔案複製和寫入登錄項目，例如，您撰寫資料列和資料行包含檔案和登錄資料的資料庫資料表中。  
  
## <a name="database-entries"></a>資料庫項目  
 若要安裝 VSPackage，Windows Installer 套件必須包含資料庫項目，以執行下列工作：  
  
-   搜尋來尋找舊版系統[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 支援 （使用 Windows Installer 表格包含 AppSearch、 CompLocator、 RegLocator、 DrLocator，以及簽章）。  
  
-   如果不支援的版本，請取消安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝或如果 （使用 LaunchCondition 資料表） 不符合另一個系統需求的 VSPackage。  
  
-   安裝 VSPackage 和相依的檔案 （使用目錄、 元件和檔案表格）。  
  
-   新增適當的資訊，vspackage 登錄 （使用登錄資料表）。  
  
-   整合在 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由呼叫**devenv.exe /setup** （使用 CustomAction 資料表）。  
  
 如需詳細資訊，請參閱[Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## <a name="setup-tools"></a>安裝程式工具  
 許多協力廠商安裝程式工具提供用於 Windows Installer 封裝的開發環境。 兩個免費工具，如下所示：  
  
-   InstallShield 限量版  
  
     您可以透過 Visual Studio 取得 InstallShield 的受限的版本**新專案**對話方塊。 展開**其他專案類型**，然後選取 **安裝和部署**。 選取的 InstallShield 範本。  
  
-   Windows Installer XML Toolset  
  
     工具組會建置 XML 來源檔案從 Windows Installer 封裝。 工具組是 Microsoft 的開放原始碼專案。 您可以下載的原始程式碼和可執行檔從[http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix)。  
  
 適用於整合到商業產品[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，請參閱[http://visualstudiogallery.com](http://visualstudiogallery.com/)。  
  
## <a name="see-also"></a>請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)