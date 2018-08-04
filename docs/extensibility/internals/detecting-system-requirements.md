---
title: 偵測系統需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a794391001934164e52bdd73d940cb73ff3b5f3b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500078"
---
# <a name="detect-system-requirements"></a>偵測系統需求
VSPackage 才能運作，除非已安裝 Visual Studio。 當您使用 Microsoft Windows Installer 管理 VSPackage 的安裝時，您可以設定以偵測是否已安裝 Visual Studio 安裝程式。 您也可以設定以檢查系統有任何其他需求，例如，特定版本的 Windows 或特定的 RAM 數量。  
  
## <a name="detect-visual-studio-editions"></a>偵測到 Visual Studio 版本  
 若要判斷是否已安裝的 Visual Studio 版本，請確認的值**安裝**登錄機碼已 *(REG_DWORD) 1*與下表中列出的適當資料夾中。 請注意，Visual Studio 版本的階層：  
  
1.  企業  
  
2.  Professional  
  
3.  社群  
      
安裝較新版本時，該版本的登錄機碼會與較早版本也加入。 也就是，如果安裝 Enterprise edition，則**安裝**金鑰設為*1*企業的需求，以及 Professional 及 Community 版。 因此，您需要只會檢查您所需要的最新版本。  
  
> [!NOTE]
>  在登錄編輯程式的 64 位元版本，32 位元的金鑰會顯示下**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**。 Visual Studio 金鑰受到**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**。  
  
|產品|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell （整合和獨立模式）|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Visual Studio 執行時偵測  
 如果安裝 VSPackage 時，Visual Studio 正在執行，無法正確地註冊 VSPackage。 安裝程式必須偵測 Visual Studio 執行時，並拒絕安裝程式。 Windows 安裝程式不會讓您使用資料表項目，若要啟用這類的偵測。 相反地，您必須建立自訂的動作，如下所示： 使用`EnumProcesses`函式來偵測*devenv.exe*處理，然後設定使用的安裝程式屬性中的啟動條件或有條件地顯示的對話方塊會提示使用者在關閉 Visual Studio。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)