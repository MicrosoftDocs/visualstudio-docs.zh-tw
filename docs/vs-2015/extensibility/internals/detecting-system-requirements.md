---
title: 偵測系統需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1956130203498d32d1ee39d67121f7797dd41fc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187469"
---
# <a name="detecting-system-requirements"></a>偵測系統需求
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 才能運作，除非已安裝 Visual Studio。 當您使用 Microsoft Windows Installer 管理 VSPackage 的安裝時，您可以設定以偵測是否已安裝 Visual Studio 安裝程式。 您也可以設定以檢查系統有任何其他需求，例如，特定版本的 Windows 或特定的 RAM 數量。  
  
## <a name="detecting-visual-studio-editions"></a>偵測 Visual Studio 版本  
 若要判斷是否已安裝的 Visual Studio 版本，確認安裝登錄機碼的值 (REG_DWORD) 1 在適當的資料夾中下, 表所示。 請注意，Visual Studio 版本的階層：  
  
1.  企業  
  
2.  Professional  
  
3.  社群  
  
 安裝 「 更高 」 的版本時，會加入該版本也與 「 低 」 版本的登錄機碼。 也就是如果安裝 Enterprise edition，則安裝機碼設為 1 的 Enterprise、 以及 Professional 及 Community 版。 因此，您必須只會檢查您所需要的 「 高 」 版本。  
  
> [!NOTE]
>  在登錄編輯程式的 64 位元版本，32 位元的金鑰會顯示下 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\。 Visual Studio 金鑰受到 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\。  
  
|產品|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell （整合和獨立模式）|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio 執行時偵測  
 如果安裝 VSPackage 時，Visual Studio 正在執行，無法正確地註冊 VSPackage。 安裝程式必須偵測 Visual Studio 執行時，並拒絕安裝程式。 Windows 安裝程式不會讓您使用資料表項目，若要啟用這類的偵測。 相反地，您必須建立自訂的動作，如下所示： 使用`EnumProcesses`函式來偵測的 devenv.exe 處理序，並接著設定中的啟動條件或有條件地使用安裝程式屬性會顯示一個對話方塊，提示使用者關閉Visual Studio。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

