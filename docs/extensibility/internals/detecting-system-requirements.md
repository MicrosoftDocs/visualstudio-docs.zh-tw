---
title: 檢測系統要求 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708740"
---
# <a name="detect-system-requirements"></a>偵測系統要求
除非安裝了 Visual Studio,否則 VS 包無法正常工作。 當您使用 Microsoft Windows 安裝程式管理 VSPackage 的安裝時,可以設定安裝程式以檢測是否安裝了 Visual Studio。 您還可以將其設定為檢查系統是否具有其他要求,例如,特定版本的 Windows 或特定數量的 RAM。

## <a name="detect-visual-studio-editions"></a>偵測視覺工作室版本
 要確定是否安裝了 Visual Studio 版本,請驗證**安裝**註冊表項的值是否為相應資料夾中 *(REG_DWORD 如下表中列出的)1。* 請注意,有視覺工作室版本的層次結構:

1. Enterprise

2. Professional

3. 社群

安裝較新版本後,將添加該版本的註冊表項以及早期版本的註冊表項。 也就是說,如果安裝了企業版,則**安裝密鑰設置為** *1*面向企業版以及專業版和社區版。 因此,您只需檢查所需的最新版本。

> [!NOTE]
> 在註冊錶編輯器的 64 位元版本中,32 位元鍵顯示在**HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node\\**下。 視覺工作室鍵在**HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node_微軟_DevDiv_vs_\\服務**。

|Products|Key|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE_軟體_微軟_DevDiv_vs_服務\14.0\企業|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE_軟體_微軟_DevDiv_vs_服務\14.0\專業|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE_SOFTWARE_微軟_DevDiv_vs_服務\14.0\社區|
|視覺工作室 2015 外殼(集成和隔離)|HKEY_LOCAL_MACHINE_SOFTWARE_微軟_DevDiv_vs_服務\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>偵測視覺化工作室何時執行
 如果安裝 VSPackage 時 Visual Studio 正在運行,則無法正確註冊您的 VS 包。 安裝程式必須檢測 Visual Studio 何時運行,然後拒絕安裝程式。 Windows 安裝程式不允許使用表條目啟用此類檢測。 相反,您必須創建一個自定義操作,如下所示:使用`EnumProcesses`函數檢測*devenv.exe*進程,然後設置在啟動條件中使用的安裝程式屬性,或者有條件地顯示一個對話框,提示使用者關閉 Visual Studio。

## <a name="see-also"></a>另請參閱
- [使用 Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
