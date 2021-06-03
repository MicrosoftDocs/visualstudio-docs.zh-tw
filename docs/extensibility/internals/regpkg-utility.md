---
title: RegPkg 公用程式 |Microsoft Docs
description: 瞭解 RegPkg.exe 公用程式如何向 Visual Studio 註冊 VSPackage，並將它準備好進行部署。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffef522cb85816c36bee1cb623810fb254d1ddec
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351938"
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方式是使用 .pkgdef 檔。 這可讓您進行擴充部署，而不需要存取系統登錄，這是 VSIX 部署的需求。 .Pkgdef 檔案是使用 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。 如需 Visual Studio 套件部署的詳細資訊，請參閱 [運送 Visual Studio 擴充](../../extensibility/shipping-visual-studio-extensions.md)功能。

 RegPkg.exe 公用程式會向註冊 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並準備部署。 此公用程式會在 VSPackage 開發期間用於幕後。 它會執行為組建程式的一部分，讓您可以在實驗 hive 中建立和執行 VSPackage。

 RegPkg 可以用數種格式產生系統登錄腳本。 您可以將這些腳本併入部署專案中，例如 .msi 專案或 Windows Installer XML 工具組檔案。

 RegPkg.exe 通常位於 \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 遵循下列語法：

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root： root 在指定的根目錄下執行註冊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 /regfile： FileName 會建立 .reg 檔，而不是更新登錄。  無法搭配/vrgfile 或/rgsfile 或/wixfile. 使用

 /rgsfile： FileName 會建立 .rgs 檔案，而不是更新登錄。  無法搭配/vrgfile 或/regfile 或/wixfile. 使用

 /vrgfile： FileName 會建立 vrg 檔案，而不是更新登錄。  無法搭配/regfile 或/rgsfile 或/wixfile. 使用

 除了 rgs 檔案之外，/rgm 還會建立 rgm 檔案。  必須搭配/rgsfile。

 /wixfile： FileName 會建立 Windows Installer 的 XML 工具組相容檔案，而不是更新登錄。  無法搭配/regfile 或/rgsfile 或/vrgfile. 使用

 /codebase 強制註冊程式碼基底，而不是元件。

 /assembly 會強制註冊元件，而不是程式碼基底。

 /unregister 取消註冊此封裝。  無法使用

 使用/regfile 或/vrgfile 或/rgsfile 或/wixfile。

## <a name="see-also"></a>另請參閱
- [VSPackages](../../extensibility/internals/vspackages.md)
- [針對 RegPkg 套件註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
