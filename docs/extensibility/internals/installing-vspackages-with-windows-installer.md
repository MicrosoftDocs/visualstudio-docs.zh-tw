---
title: 使用 Windows Installer 安裝 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cd5f25e1e87ba3db360b328b4f5a245697cba45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860252"
---
# <a name="installing-vspackages-with-windows-installer"></a>使用 Windows Installer 安裝 VSPackage
整合到 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]需要不只將檔案複製到使用者的電腦。 VSPackage 的安裝程式必須安裝 VSPackage 和其相依的檔案，並註冊及整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 VSPackage 可以利用整合功能，例如上顯示圖示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]啟動顯示畫面和 [關於] 對話方塊。

 Microsoft Windows Installer 檔案的建議方式是將您的 Vspackage。 方便使用 Windows Installer 封裝可以在 支援的任何 Windows 作業系統上執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 < [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)。

## <a name="in-this-section"></a>本節內容
- [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)

 提供 Windows 安裝程式的概觀。

- [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)

 討論您可以在支援的兩個 Vspackage 的並排顯示安裝的不同方式和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

- [撰寫 Windows Installer 封裝](../../extensibility/internals/authoring-a-windows-installer-package.md)

 提供的安裝程式會遵循正確安裝，並整合至 Vspackage 的一般步驟概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)

 描述如何偵測安裝程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和元件與取消設定如果不符合 VSPackage 需求。

- [元件管理](../../extensibility/internals/component-management.md)

 討論如何開發的安裝程式會維護舊版產品的完整性。

- [選擇 VSPackage 的安裝目錄](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 摘要說明尋找 Vspackage 的選項。

- [VSPackage 註冊](../../extensibility/internals/vspackage-registration.md)

 討論 Vspackage 在安裝期間註冊的方式和原因自我登錄是個好主意。

- [部署專案類型](../../extensibility/internals/deploying-project-types.md)

 討論如何使用新的專案類型彙總工具適用於 managed 程式碼專案類型。

- [如何：產生安裝程式的登錄資訊](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 說明如何使用 RegPkg.exe 產生 managed VSPackage 註冊資訊清單。

- [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 說明如何執行後續安裝命令，以整合到 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

- [使用 Windows Installer 解除安裝 VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 說明當使用者解除安裝 VSPackage 時，必須執行安裝程式的步驟。