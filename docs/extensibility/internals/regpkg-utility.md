---
title: RegPkg 公用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3f9eecfaeffd19ece7e0ca2fe14e3f95556503d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904873"
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
> [!NOTE]
>  Visual Studio 中註冊套件的慣用的方法是使用.pkgdef 檔案。 這可讓擴充功能部署而不需要存取系統登錄，也就是 VSIX 部署的需求。 使用建立 Pkgdef 檔案[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。 如需有關 Visual Studio 封裝部署的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 公用程式註冊使用 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並準備好進行部署。 VSPackage 開發期間，此公用程式會在幕後使用的。 它會執行建置程序的一部分，讓您可以建置和執行在實驗登錄區中的 VSPackage。  
  
 RegPkg 可以產生系統登錄指令碼，以數種格式。 您可以將這些指令碼，在部署專案，例如.msi 專案或 Windows Installer XML 工具組的檔案。  
  
 RegPkg.exe 通常是位於\< *Visual Studio SDK 安裝路徑*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 遵循此語法：  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 執行下指定的註冊  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根目錄。  
  
 /regfile:FileName  
 建立的.reg 檔案，而不是更新登錄。  不搭配 /vrgfile /rgsfile 或 /wixfile。  
  
 /rgsfile:FileName  
 建立.rgs 檔案，而不是更新登錄。  不搭配 /vrgfile /regfile 或 /wixfile。  
  
 /vrgfile:FileName  
 建立.vrg 檔案，而不是更新登錄。  不搭配 /regfile /rgsfile 或 /wixfile。  
  
 /rgm  
 建立.rgm 檔案除了 rgs 檔。  必須與 /rgsfile 結合。  
  
 /wixfile:FileName  
 建立 Windows Installer XML 工具組相容的檔案，而不是更新登錄。  不搭配 /regfile /rgsfile 或 /vrgfile。  
  
 /codebase  
 強制使用程式碼基底，而不是組件的註冊。  
  
 /assembly  
 強制使用組件，而不是程式碼基底的註冊。  
  
 / 取消註冊  
 取消註冊此套件。  無法使用  
  
 /regfile 或 /vrgfile 或 /rgsfile 或 /wixfile。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 [對 RegPkg 封裝註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)