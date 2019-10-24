---
title: RegPkg 公用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724440"
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
> [!NOTE]
> 在 Visual Studio 中註冊封裝的慣用方法是使用 .pkgdef 檔案。 這可讓您擴充部署，而不需要存取系統登錄，這是 VSIX 部署的需求。 .Pkgdef 檔案是使用[CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)建立的。 如需 Visual Studio 套件部署的詳細資訊，請參閱[運送 Visual Studio 延伸](../../extensibility/shipping-visual-studio-extensions.md)模組。

 RegPkg 公用程式會向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 註冊 VSPackage，並準備好進行部署。 這個公用程式會在 VSPackage 開發期間于幕後使用。 它會在組建程式中執行，讓您可以在實驗 hive 中建立及執行 VSPackage。

 RegPkg 可以產生數種格式的系統登錄腳本。 您可以將這些腳本併入部署專案中，例如 .msi 專案或 Windows Installer XML 工具組檔案。

 RegPkg 通常位於 \<*VISUAL STUDIO SDK 安裝路徑*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe。 RegPkg 會遵循下列語法：

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root： root 在指定的下執行註冊

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根。

 /regfile： FileName 會建立一個 .reg 檔案，而不是更新登錄。  不能搭配/vrgfile 或/rgsfile 或/wixfile. 使用

 /rgsfile： FileName 會建立 .rgs 檔案，而不是更新登錄。  不能搭配/vrgfile 或/regfile 或/wixfile. 使用

 /vrgfile： FileName 會建立 vrg 檔案，而不是更新登錄。  不能搭配/regfile 或/rgsfile 或/wixfile. 使用

 除了 rgs 檔案之外，/rgm 還會建立 rgm 檔案。  必須與/rgsfile. 結合

 /wixfile： FileName 會建立與 Windows Installer XML 工具組相容的檔案，而不是更新登錄。  不能搭配/regfile 或/rgsfile 或/vrgfile. 使用

 /codebase 會強制使用程式碼基底（而不是元件）進行註冊。

 /assembly 會強制使用元件註冊，而不是程式碼基底。

 /unregister 會取消註冊此封裝。  無法使用

 使用/regfile 或/vrgfile 或/rgsfile 或/wixfile。

## <a name="see-also"></a>請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)
- [對 RegPkg 封裝註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)