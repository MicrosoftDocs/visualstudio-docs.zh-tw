---
title: "RegPkg 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4a4a3481b6ff1a5b8af0581e2c04602073adeae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
> [!NOTE]
>  註冊套件在 Visual Studio 中的慣用的方法是使用.pkgdef 檔。 這可讓擴充部署不需要存取系統登錄中，是 VSIX 部署的需求。 使用建立 Pkgdef 檔案[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。 如需有關 Visual Studio 封裝部署的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 公用程式註冊 VSPackage 與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並準備進行部署。 VSPackage 開發期間，此公用程式會使用背後的運作原理。 它會執行建置流程的一部分，讓您可以建置並執行實驗登錄區中的 VSPackage。  
  
 RegPkg 可以數種格式產生系統登錄指令碼。 您可以合併這些指令碼，在部署專案，例如.msi 專案或 Windows Installer XML 工具組檔案。  
  
 RegPkg.exe 通常是位於\< *Visual Studio SDK 安裝路徑*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 遵循此語法：  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 執行指定之下註冊  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根節點。  
  
 /regfile:FileName  
 建立的.reg 檔案，而不會更新登錄。  不能與 /vrgfile 或 /rgsfile /wixfile。  
  
 /rgsfile:FileName  
 建立.rgs 檔案，而不會更新登錄。  不能與 /vrgfile 或 /regfile /wixfile。  
  
 /vrgfile:FileName  
 建立.vrg 檔案，而不會更新登錄。  不能與 /regfile 或 /rgsfile /wixfile。  
  
 /rgm  
 建立.rgm 檔案除了 rgs 檔。  必須與 /rgsfile 結合。  
  
 /wixfile:FileName  
 建立 Windows Installer XML 工具組相容檔案，而不會更新登錄。  不能與 /regfile 或 /rgsfile /vrgfile。  
  
 /codebase  
 強制使用程式碼基底，而不是組件的註冊。  
  
 /assembly 選項  
 強制註冊組件，而不是程式碼基底。  
  
 / 取消註冊  
 取消註冊此封裝。  無法使用  
  
 /regfile 或 /vrgfile 或 /rgsfile 或 /wixfile。  
  
## <a name="see-also"></a>請參閱  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 [對 RegPkg 封裝註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)