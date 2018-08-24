---
title: 撰寫的 Windows Installer 套件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edb0a1d385129600372fc26693aec729751a768c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512864"
---
# <a name="author-a-windows-installer-package"></a>撰寫的 Windows Installer 套件
資料磁碟機的 Windows 安裝程式的模型。 而非撰寫程序的指令碼，以將檔案複製和寫入登錄項目，例如，您撰寫資料列和資料行包含檔案和登錄資料的資料庫資料表中。  
  
## <a name="database-entries"></a>資料庫項目  
若要安裝 VSPackage，Windows 安裝程式套件必須包含資料庫項目，以執行下列工作：  
  
- 搜尋系統以找出的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 支援 （使用 Windows Installer 的資料表，包括 AppSearch、 CompLocator、 RegLocator、 DrLocator，以及簽章）。  
  
- 如果沒有支援的版本，請取消安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝則 VSPackage 的其他系統需求不相符 （使用 LaunchCondition 資料表）。  
  
- 安裝 VSPackage 和相依的檔案 （使用 directory、 元件和檔案資料表）。  
  
- 新增適當的資訊，vspackage 登錄 （Registry 資料表）。  
  
- 整合在 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由呼叫**devenv.exe /setup** （使用 CustomAction 資料表）。  
  
如需詳細資訊，請參閱 < [Windows Installer](/windows/desktop/Msi/windows-installer-portal)。
  
## <a name="setup-tools"></a>安裝程式工具  
有各式各樣的協力廠商安裝程式工具會提供 Windows Installer 封裝的開發環境。 會有下列的免費工具：  
  
- InstallShield 限量版  
  
   您可以透過 Visual Studio 中取得的精簡的版本的 InstallShield**新的專案**對話方塊。 依序展開**其他專案類型**，然後選取**安裝和部署**。 選取 InstallShield 範本。  
  
- Windows Installer XML 工具組  
  
   Windows Installer XML (WiX) 工具組建置 XML 原始程式檔的 Windows Installer 封裝。 WiX 工具組是 Microsoft 的開放原始碼專案。 您可以下載原始程式碼和可執行檔[Wix 工具組](http://sourceforge.net/projects/wix)。  
  
   適用於整合的商業產品[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]利用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，請參閱[ http://visualstudiogallery.com ](http://visualstudiogallery.com/)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)