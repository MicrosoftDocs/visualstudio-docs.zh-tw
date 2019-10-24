---
title: 卸載具有 Windows Installer 的 VSPackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722137"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>使用 Windows Installer 解除安裝 VSPackage
在大部分的情況下，Windows Installer 可以藉由「復原」安裝 VSPackage 的功能來卸載 VSPackage。 在[安裝後必須執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)中所討論的自訂動作，必須在卸載之後才執行。 由於在安裝和卸載的 InstallFinalize 標準動作之前，會呼叫 devenv .exe，因此 CustomAction 和 InstallExecuteSequence 資料表專案會為這兩種情況提供服務。

> [!NOTE]
> 卸載 MSI 套件之後，請執行 `devenv /setup`。

 一般來說，如果您將自訂動作新增至 Windows Installer 套件，就必須在卸載和回復期間處理這些動作。 例如，如果您新增自訂動作以自我註冊您的 VSPackage，您也必須新增自訂動作來將它取消登錄。

> [!NOTE]
> 使用者可以安裝您的 VSPackage，然後卸載與它整合的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本。 您可以藉由排除在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 上執行具有相依性之程式碼的自訂動作，協助確保您的 VSPackage 卸載在該案例中運作。

## <a name="handling-launch-conditions-at-uninstall-time"></a>在卸載時處理啟動條件
 如果不符合條件，LaunchConditions 標準動作會讀取 LaunchCondition 資料表的資料列，以顯示錯誤訊息。 由於啟動條件通常是用來確保符合系統需求，因此您通常可以藉由在 LaunchCondition 資料表的 LaunchConditions 資料列中加入條件 `NOT Installed`，在卸載期間略過啟動條件。

 另一個替代方法是新增 `OR Installed`，以在卸載期間啟動不重要的條件。 這可確保在卸載期間，條件一律為 true，因此不會顯示啟動條件錯誤訊息。

> [!NOTE]
> `Installed` 是偵測到系統上已安裝您的 VSPackage 時，Windows Installer 設定的屬性。

## <a name="see-also"></a>請參閱
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)