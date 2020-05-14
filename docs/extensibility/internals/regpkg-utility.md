---
title: RegPkg 實用程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705642"
---
# <a name="regpkg-utility"></a>RegPkg 公用程式
> [!NOTE]
> 在 Visual Studio 中註冊包的首選方法是使用 .pkgdef 檔。 這允許擴展部署,而無需訪問系統註冊表,這是 VSIX 部署的要求。 Pkgdef 檔案是透過使用[CreatePkgDef 實用程式](../../extensibility/internals/createpkgdef-utility.md)創建的。 有關可視化工作室包部署的詳細資訊,請參閱[傳送視覺工作室擴展](../../extensibility/shipping-visual-studio-extensions.md)。

 RegPkg.exe 實用程式註冊 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並為其進行部署。 此實用程式在 VSPackage 開發期間在後台使用。 它作為生成過程的一部分運行,以便您可以在實驗配置單元中生成和運行 VSPackage。

 RegPkg 可以生成多種格式的系統註冊錶腳本。 您可以將這些文本合併到部署專案中,如 .msi 專案或 Windows 安裝程式 XML 工具集檔。

 RegPkg.exe 通常\<位於*視覺工作室 SDK 安裝路徑*>_VisualStudio 整合的\工具\Bin_RegPkg.exe。 RegPkg 遵循以下語法:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:根在指定下執行註冊

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根帳戶

 /regfile:Filename 創建一個 .reg 檔案,而不是更新註冊表。  不能與 /vrgfile 或 /rgsfile 或 /wixfile 一起使用。

 /rgsfile:Filename 創建一個 .rgs 檔案,而不是更新註冊表。  不能與 /vrgfile 或 /regfile 或 /wixfile 一起使用。

 /vrgfile:Filename 創建一個 .vrg 檔,而不是更新註冊表。  不能與 /regfile 或 /rgsfile 或 /wixfile 一起使用。

 /rgm 除了 rgs 檔之外,還創建一個 .rgm 檔。  必須與 /rgsfile 組合。

 /wixfile:檔案名創建一個 Windows 安裝程式 XML 工具集相容檔,而不是更新註冊表。  不能與 /regfile 或 /rgsfile 或 /vrgfile 一起使用。

 /代碼庫 強制註冊代碼庫,而不是程式集。

 /程式集強制註冊程式集,而不是代碼庫。

 /取消註冊取消註冊此包。  無法使用

 帶 /regfile 或 /vrgfile 或 /rgsfile 或 /wixfile。

## <a name="see-also"></a>另請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)
- [針對 RegPkg 套件註冊進行疑難排解](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
