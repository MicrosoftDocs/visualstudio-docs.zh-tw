---
title: 使用 Windows Installer 安裝 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687471"
---
# <a name="installing-vspackages-with-windows-installer"></a>使用 Windows Installer 安裝 VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

將您的 VSPackage 整合到 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 需要的不只是將檔案複製到使用者的電腦。 VSPackage 的安裝程式必須安裝 VSPackage 和其相依的檔案，並將其註冊並整合到中 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 您的 VSPackage 可以利用整合功能，例如在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 啟動顯示畫面和 [關於] 對話方塊中顯示圖示。  
  
 Microsoft Windows Installer 檔案是散發 Vspackage 的建議方式。 便於使用 Windows Installer 套件可以在支援的任何 Windows 作業系統上執行 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 如需詳細資訊，請參閱 [Windows Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
## <a name="in-this-section"></a>本節內容  
 [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)  
 提供 Windows Installer 的總覽。  
  
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)  
 討論各種不同的方式，可支援您 Vspackage 和的並存安裝 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [編寫 Windows Installer 套件](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 概述安裝程式遵循正確安裝和整合 Vspackage 至的一般步驟 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)  
 描述安裝程式如何偵測 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 和其元件，並在不符合 VSPackage 需求時取消安裝程式。  
  
 [元件管理](../../extensibility/internals/component-management.md)  
 討論如何開發將維持舊版產品完整性的安裝程式。  
  
 [選擇 VSPackage 的安裝目錄](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 摘要說明用來尋找 Vspackage 的選項。  
  
 [VSPackage 註冊](../../extensibility/internals/vspackage-registration.md)  
 討論在安裝期間如何註冊 Vspackage，以及為什麼自我註冊是不好的想法。  
  
 [部署專案類型](../../extensibility/internals/deploying-project-types.md)  
 討論如何針對 managed 程式碼專案類型使用新的專案類型匯總工具。  
  
 [如何︰產生安裝程式的登錄資訊](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 說明如何使用 RegPkg.exe 來產生受控 VSPackage 的註冊資訊清單。  
  
 [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 說明如何執行後續安裝命令，以將 Vspackage 整合到中 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [使用 Windows Installer 解除安裝 VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 描述當使用者卸載您的 VSPackage 時，您的安裝程式必須執行的步驟。  
  
## <a name="related-sections"></a>相關章節  
 [安裝 VSPackage](../../misc/installing-vspackages.md)  
 討論如何建立和安裝 Vspackage，以及如何支援同時執行多個版本的使用者 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。
