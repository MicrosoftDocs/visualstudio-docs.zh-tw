---
title: 使用 Windows 安裝程式安裝 VS 包 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707467"
---
# <a name="installing-vspackages-with-windows-installer"></a>使用 Windows Installer 安裝 VSPackage
將 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合到其中不僅需要將檔案複製到使用者的電腦。 VSPackage 的安裝程式必須安裝 VSPackage 及其相關檔案,並註冊它們並將其[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合到中 。 您的 VSPackage 可以利用整合功能,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]例如在初始螢幕上顯示圖示和「關於」對話框。

 Microsoft Windows 安裝程式檔是分發 VS 包的推薦方式。 易於使用的 Windows 安裝程式包[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以在支援的任何 Windows 作業系統上運行。 有關詳細資訊,請參閱[Windows 安裝程式](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)。

## <a name="in-this-section"></a>本節內容
- [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)

 提供 Windows 安裝程式的概述。

- [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)

 討論支援並行安裝 VS[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包和 的不同方法。

- [編寫 Windows Installer 套件](../../extensibility/internals/authoring-a-windows-installer-package.md)

 概述安裝程式為正確安裝 VS 套件並將其整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中 所遵循的典型步驟。

- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)

 描述安裝程式如何檢測[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]其元件,並在不符合 VSPackage 要求時取消設置。

- [元件管理](../../extensibility/internals/component-management.md)

 討論如何開發一個安裝程式,將保持以前產品版本的完整性。

- [選擇 VSPackage 的安裝目錄](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 總結了尋找 VSPackages 的選項。

- [VSPackage 註冊](../../extensibility/internals/vspackage-registration.md)

 討論如何在安裝時註冊 VSPackages,以及為什麼自註冊是一個壞主意。

- [部署專案類型](../../extensibility/internals/deploying-project-types.md)

 討論如何將新的項目類型聚合器用於託管代碼項目類型。

- [如何︰產生安裝程式的登錄資訊](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 說明如何使用 RegPkg.exe 為託管 VSPackage 生成註冊清單。

- [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 說明如何運行安裝後命令以將 VS 包[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合到 中。

- [使用 Windows Installer 解除安裝 VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 描述使用者卸載您的 VSPackage 時安裝程式必須執行的步驟。
