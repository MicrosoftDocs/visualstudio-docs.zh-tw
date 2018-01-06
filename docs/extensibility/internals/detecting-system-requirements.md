---
title: "偵測系統需求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: "50"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc16c51b72ced37072c4ddf6d47bf347cf57c0f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="detecting-system-requirements"></a>偵測系統需求
VSPackage 無法作用，除非已安裝 Visual Studio。 當您使用 Microsoft Windows 安裝程式來管理您的 VSPackage 的安裝時，您可以設定來偵測是否已安裝 Visual Studio 安裝程式。 您也可以設定它來檢查系統有其他需求，例如，特定版本的 Windows 或特定的 RAM 數量。  
  
## <a name="detecting-visual-studio-editions"></a>偵測 Visual Studio 版本  
 若要判斷是否已安裝的 Visual Studio 版本中，確認安裝登錄機碼值 (REG_DWORD) 中適當的資料夾，1 為下表所列。 請注意，Visual Studio 版本的階層：  
  
1.  企業  
  
2.  Professional  
  
3.  社群  
  
 安裝 「 較高 」 的版本時，會加入該版本以及與 「 較低 」 版本的登錄機碼。 也就是如果 Enterprise edition 已安裝，安裝金鑰設為 1，企業版以及專業人員與 Community 版本。 因此，您需要只會檢查您所需要的 「 高 」 版本。  
  
> [!NOTE]
>  在登錄編輯程式的 64 位元版本中，32 位元的金鑰會顯示在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node 底下\\。 Visual Studio 金鑰受到 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\。  
  
|產品|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell （整合和獨立模式）|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio 執行時偵測  
 如果安裝 VSPackage 時，Visual Studio 會執行，無法正確登錄 VSPackage。 安裝程式必須偵測在執行 Visual Studio，並拒絕安裝程式。 Windows Installer 不讓您啟用這類偵測使用資料表項目。 相反地，您必須建立自訂動作，如下所示： 使用`EnumProcesses`函式來偵測的 devenv.exe 處理序，並接著設定用於啟動條件或有條件地 installer 屬性顯示的對話方塊，提示使用者關閉Visual Studio。  
  
## <a name="see-also"></a>請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)