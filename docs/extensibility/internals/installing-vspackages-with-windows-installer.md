---
title: Windows Installer 安裝 Vspackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fafebe0dc2bb8e13c99be8b340e7f5663a9930f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows Installer 安裝 Vspackage
整合到 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]需要不只將檔案複製到使用者的電腦。 VSPackage 的安裝程式，必須安裝 VSPackage 和其相依的檔案，並登錄及它們整合至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 VSPackage 可以利用整合功能，例如上顯示圖示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]啟動顯示畫面和 [關於] 對話方塊。  
  
 Microsoft Windows Installer 檔案的建議方式是將您的 Vspackage。 方便使用 Windows Installer 封裝可以在支援的任何 Windows 作業系統上執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)  
 提供 Windows 安裝程式的概觀。  
  
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)  
 討論您可以支援您的 Vspackage 的並存安裝不同的方式和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [撰寫 Windows Installer 封裝](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 提供的安裝程式正確安裝及整合到 Vspackage 所遵循的一般步驟概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)  
 描述如何安裝程式可以偵測到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和其元件和 [取消] 5d; 如果設定不符合 VSPackage 需求。  
  
 [元件管理](../../extensibility/internals/component-management.md)  
 討論如何開發的安裝程式會維護舊版產品的完整性。  
  
 [選擇 VSPackage 的安裝目錄](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 摘要，以便將 Vspackage 的選項。  
  
 [VSPackage 註冊](../../extensibility/internals/vspackage-registration.md)  
 討論在安裝期間登錄 Vspackage 的方式和原因自我登錄會是個好主意。  
  
 [部署專案類型](../../extensibility/internals/deploying-project-types.md)  
 討論如何使用新的專案類型彙總工具適用於 managed 程式碼專案類型。  
  
 [如何︰產生安裝程式的登錄資訊](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 說明如何使用 RegPkg.exe managed vspackage 中產生註冊資訊清單。  
  
 [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 說明如何執行後續安裝命令，以整合到 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 Windows Installer 解除安裝 VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 說明當使用者解除安裝您的 VSPackage，您的安裝程式必須執行的步驟。  