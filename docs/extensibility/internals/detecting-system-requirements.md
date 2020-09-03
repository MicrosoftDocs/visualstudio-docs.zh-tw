---
title: 偵測系統需求 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708740"
---
# <a name="detect-system-requirements"></a>偵測系統需求
除非安裝 Visual Studio，否則 VSPackage 無法運作。 當您使用 Microsoft Windows Installer 來管理 VSPackage 的安裝時，您可以設定安裝程式來偵測是否已安裝 Visual Studio。 您也可以將它設定為檢查系統是否有其他需求，例如特定版本的 Windows 或特定的 RAM 數量。

## <a name="detect-visual-studio-editions"></a>偵測 Visual Studio 版本
 若要判斷是否已安裝 Visual Studio 版本，請確認在適當的資料夾中， **安裝** 登錄機碼的值 * (REG_DWORD) 1* ，如下表所示。 請注意，有 Visual Studio 版本的階層：

1. 企業

2. Professional

3. 社群

當安裝較新的版本時，就會新增該版本的登錄機碼，以及舊版的登錄機碼。 也就是說，如果已安裝 Enterprise edition，則適用于 Enterprise 的 **安裝** 金鑰也會設定為1，而針對 Professional 和社區版本則設定為 *1* 。 因此，您只需要檢查您需要的最新版本。

> [!NOTE]
> 在64位版本的登錄編輯器中，32位索引鍵會顯示在**HKEY_LOCAL_MACHINE \software\wow6432node \\ **下。 Visual Studio 機碼位於**HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\devdiv\vs\servicing \\ **。

|產品|Key|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (整合和隔離) |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>偵測 Visual Studio 何時正在執行
 如果在安裝 VSPackage 時 Visual Studio 正在執行，則無法正確註冊您的 VSPackage。 安裝程式必須偵測 Visual Studio 正在執行，然後拒絕安裝程式。 Windows Installer 不會讓您使用資料表專案來啟用這類的偵測。 相反地，您必須建立自訂動作，如下所示：使用函式偵測 `EnumProcesses` *devenv.exe* 進程，然後設定啟動條件中所使用的安裝程式屬性，或有條件地顯示對話方塊，以提示使用者關閉 Visual Studio。

## <a name="see-also"></a>另請參閱
- [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
