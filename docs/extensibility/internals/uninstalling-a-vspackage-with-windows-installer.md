---
title: 使用 Windows Installer 卸載 VSPackage |Microsoft Docs
description: Windows Installer 可以藉由反向安裝來卸載您的 VSPackage。 瞭解如何在 Windows Installer 套件中處理自訂動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb5d0fe0e4812d66f6981ea58dfb51f19336d98b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090716"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>使用 Windows Installer 解除安裝 VSPackage
在大部分的情況下，Windows Installer 可以卸載 VSPackage，只要「復原」安裝 VSPackage 就可以了。 在安裝之後必須執行的 [命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 中所討論的自訂動作也必須在卸載之後執行。 因為對 devenv.exe 的呼叫會在安裝和卸載的 InstallFinalize 標準動作之前發生，所以 CustomAction 和 InstallExecuteSequence 資料表專案會提供這兩種情況。

> [!NOTE]
> `devenv /setup`在您卸載 MSI 套件之後執行。

 一般來說，如果您將自訂動作新增至 Windows Installer 套件，則必須在卸載和復原期間處理這些動作。 例如，如果您新增自訂動作來自行註冊 VSPackage，您也必須新增自訂動作來將其取消註冊。

> [!NOTE]
> 使用者可以安裝您的 VSPackage，然後將其所整合的版本卸載 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您可以藉由排除執行程式碼與相依性的自訂動作，協助確保 VSPackage 的卸載可在該情況下運作 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="handling-launch-conditions-at-uninstall-time"></a>在卸載時處理啟動條件
 LaunchConditions 標準動作會讀取 LaunchCondition 資料表的資料列，以在不符合條件時顯示錯誤訊息。 因為啟動條件通常是用來確保符合系統需求，所以您通常可以在卸載期間略過啟動條件，方法是將條件新增 `NOT Installed` 至 LaunchCondition 資料表的 LaunchConditions 資料列。

 替代方式是 `OR Installed` 在卸載期間新增不重要的啟動條件。 這可確保在卸載期間，條件一律為 true，因此不會顯示啟動條件錯誤訊息。

> [!NOTE]
> `Installed` 當屬性偵測到 VSPackage 已安裝在系統上時，就會設定屬性 Windows Installer。

## <a name="see-also"></a>另請參閱
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)