---
title: RegPkg 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d793097034dde050c8a3f45a1f227603e4a64d3e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484981"
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[RegPkg 公用程式](https://docs.microsoft.com/visualstudio/extensibility/internals/regpkg-utility)。  
  
> [!NOTE]
>  Visual Studio 中註冊套件的慣用的方法是使用.pkgdef 檔案。 這可讓擴充功能部署而不需要存取系統登錄，也就是 VSIX 部署的需求。 使用建立 Pkgdef 檔案[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。 如需有關 Visual Studio 封裝部署的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 公用程式註冊使用 VSPackage[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]並準備好進行部署。 VSPackage 開發期間，此公用程式會在幕後使用的。 它會執行建置程序的一部分，讓您可以建置和執行在實驗登錄區中的 VSPackage。  
  
 RegPkg 可以產生系統登錄指令碼，以數種格式。 您可以將這些指令碼，在部署專案，例如.msi 專案或 Windows Installer XML 工具組的檔案。  
  
 RegPkg.exe 通常是位於\< *Visual Studio SDK 安裝路徑*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 遵循此語法：  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 執行下指定的註冊  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 根目錄。  
  
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
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)   
 [對 RegPkg 封裝註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

