---
title: 撰寫的 Windows Installer 套件 |Microsoft Docs
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
ms.openlocfilehash: 30c941fd4f3c281dfe363d284a559bafe055451c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "59000703"
---
# <a name="authoring-a-windows-installer-package"></a>編寫 Windows Installer 套件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

資料磁碟機的 Windows 安裝程式的模型。 而非撰寫程序的指令碼，以將檔案複製和寫入登錄項目，例如，您撰寫資料列和資料行包含檔案和登錄資料的資料庫資料表中。  
  
## <a name="database-entries"></a>資料庫項目  
 若要安裝 VSPackage，Windows 安裝程式套件必須包含資料庫項目，以執行下列工作：  
  
- 搜尋系統以找出的版本[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]VSPackage 支援 （使用 Windows Installer 的資料表，包括 AppSearch、 CompLocator、 RegLocator、 DrLocator，以及簽章）。  
  
- 如果沒有支援的版本，請取消安裝[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]安裝則 VSPackage 的其他系統需求不相符 （使用 LaunchCondition 資料表）。  
  
- 安裝 VSPackage 和相依的檔案 （使用 directory、 元件和檔案資料表）。  
  
- 新增適當的資訊，vspackage 登錄 （Registry 資料表）。  
  
- 整合在 VSPackage[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]藉由呼叫**devenv.exe /setup** （使用 CustomAction 資料表）。  
  
  如需詳細資訊，請參閱 < [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## <a name="setup-tools"></a>安裝程式工具  
 有各式各樣的協力廠商安裝程式工具會提供 Windows Installer 封裝的開發環境。 兩個免費的工具，如下所示：  
  
- InstallShield 限量版  
  
   您可以透過 Visual Studio 中取得的精簡的版本的 InstallShield**新的專案**對話方塊。 依序展開**其他專案類型**，然後選取**安裝和部署**。 選取 InstallShield 範本。  
  
- Windows Installer XML Toolset  
  
   工具組建置 XML 原始程式檔的 Windows Installer 封裝。 工具組是 Microsoft 的開放原始碼專案。 您可以下載原始程式碼和可執行檔[ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix)。  
  
  適用於整合的商業產品[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]利用[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]，請參閱[ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
