---
title: 撰寫 Windows Installer 套件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301134"
---
# <a name="authoring-a-windows-installer-package"></a>編寫 Windows Installer 套件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

資料會驅動 Windows Installer 模型。 例如，您可以撰寫包含檔案和登錄資料的資料庫資料表中的資料列和資料行，而不是編寫程式腳本來複製檔案和寫入登錄專案。  
  
## <a name="database-entries"></a>資料庫項目  
 若要安裝 VSPackage，Windows Installer 封裝必須包含資料庫專案，才能執行下列工作：  
  
- 搜尋系統，找出 VSPackage 支援的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 版本（使用包含 AppSearch、CompLocator、RegLocator、DrLocator 和 Signature 的 Windows Installer 資料表）。  
  
- 如果未安裝支援的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 版本，或不符合 VSPackage 的另一個系統需求（使用 LaunchCondition 資料表），則取消安裝。  
  
- 安裝 VSPackage 和相依檔案（使用目錄、元件和檔案資料表）。  
  
- 將 VSPackage 的適當資訊新增至登錄（使用登錄資料表）。  
  
- 藉由呼叫**devenv/setup** （使用 CustomAction 資料表）來整合 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的 VSPackage。  
  
  如需詳細資訊，請參閱[Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## <a name="setup-tools"></a>安裝工具  
 各種協力廠商安裝工具提供 Windows Installer 套件的開發環境。 兩個免費工具如下：  
  
- InstallShield 限量版  
  
   您可以透過 Visual Studio 的 [**新增專案**] 對話方塊取得受限版本的 InstallShield。 展開 [**其他專案類型**]，然後選取 [**安裝和部署**]。 選取 [InstallShield] 範本。  
  
- Windows Installer XML Toolset  
  
   工具組會建立 XML 來源檔案 Windows Installer 套件。 工具組是 Microsoft 開放原始碼專案。 您可以從[http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/)下載原始程式碼和可執行檔。  
  
  如需使用 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]整合到 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的商業產品，請參閱[https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
